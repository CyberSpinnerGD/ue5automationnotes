**Instancias de Material en UE5:**

1. **Instancia de Material Estática (Static/Constant Material Instance):**
    
    - Configurada antes del tiempo de ejecución.
    - No se puede modificar durante el juego.
    - Mejora la eficiencia y el rendimiento.
    - Ideal para materiales que no necesitan cambiar​ ([Epic Dev | Home](https://dev.epicgames.com/documentation/en-us/unreal-engine/instanced-materials-in-unreal-engine#:~:text=URL%3A%20https%3A%2F%2Fdev.epicgames.com%2Fdocumentation%2Fen))​​ ([Unreal Engine Documentation](https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/Materials/HowTo/Instancing/))​.
2. **Instancia de Material Dinámica (Dynamic Material Instance):**
    
    - Permite modificaciones en tiempo de ejecución.
    - Útil para cambios en respuesta a eventos del juego (como cambiar color, transparencia, etc.).
    - Creada y ajustada continuamente durante el juego usando Blueprint o C++​ ([Epic Dev | Home](https://dev.epicgames.com/community/learning/tutorials/dD6/unreal-engine-dynamic-material-instances-part-1-tweaking-materials-at-runtime#:~:text=URL%3A%20https%3A%2F%2Fdev.epicgames.com%2Fcommunity%2Flearning%2Ftutorials%2FdD6%2Funreal))​​ ([Unreal Engine Documentation](https://docs.unrealengine.com/4.26/en-US/BlueprintAPI/Rendering/Material/CreateDynamicMaterialInstance/))​.
      
En Unreal Engine, cuando se carga un asset sin especificar el tipo de instancia, el tipo por defecto depende del tipo de asset en sí mismo. Para materiales, la instancia que se carga dependerá del tipo de material referenciado. Aquí hay una explicación más detallada:

1. **Instancia de Material Constante (MaterialInstanceConstant)**:
    
    - Si el asset que estás cargando es explícitamente una instancia constante, como se muestra en tu ejemplo, la carga especificará que es de tipo `MaterialInstanceConstant`. Estas son instancias que se configuran antes del tiempo de ejecución y no cambian durante el juego.
    
    python
    
    
    
    `asset: unreal.MaterialInstanceConstant = EAL.load_asset("/Game/StarterContent/Materials/example_ins.example_ins'")`
    
2. **Material Base o Material Puro**:
    
    - Si no se especifica que el material es una instancia constante o dinámica y simplemente se carga un material sin más, el tipo por defecto sería el material base (`Material`). Este tipo de material no tiene parámetros configurables como las instancias de material.
    
    python
    
    
    
    `asset: unreal.Material = EAL.load_asset("/Game/StarterContent/Materials/example_base.example_base'")`
    
3. **Instancia de Material Dinámica (MaterialInstanceDynamic)**:
    
    - Si necesitas una instancia dinámica que pueda ser modificada en tiempo de ejecución, normalmente se crea una instancia dinámica a partir de un material base o de una instancia constante usando métodos específicos en el código, como `CreateDynamicMaterialInstance`.
    
    python
    

    
    `dynamic_material_instance = EAL.create_dynamic_material_instance(asset)`
    

En resumen, si no se especifica el tipo al cargar un material, por defecto se cargará como el tipo base del asset, que usualmente es un `Material`. Las instancias de material, ya sean constantes o dinámicas, necesitan ser especificadas o creadas explícitamente en el código​ ([Epic Dev | Home](https://dev.epicgames.com/documentation/en-us/unreal-engine/instanced-materials-in-unreal-engine#:~:text=URL%3A%20https%3A%2F%2Fdev.epicgames.com%2Fdocumentation%2Fen))​​ ([Unreal Engine Documentation](https://docs.unrealengine.com/4.26/en-US/BlueprintAPI/Rendering/Material/CreateDynamicMaterialInstance/))​​ ([Assembla](https://get.assembla.com/blog/perforce-vs-git/))​.
Para más detalles, consulta la [documentación oficial de Unreal Engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/instanced-materials-in-unreal-engine).