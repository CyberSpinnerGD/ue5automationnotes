### Documentación para Cambiar y Guardar Parámetros de una Instancia de Material en Unreal Engine con Python

#### Descripción

Este documento proporciona una guía sobre cómo cambiar un parámetro vectorial en una instancia de material y guardar los cambios de forma programática en Unreal Engine usando Python.

#### Requisitos

- Unreal Engine instalado
- Acceso a la API de Python de Unreal Engine
- Material existente en el proyecto

#### Pasos

1. **Importar las Bibliotecas Necesarias**
   ```python
   import unreal
   ```

2. **Definir la Función para Cambiar el Parámetro y Guardar el Material**
   ```python
   def set_material_vector(material_instance: unreal.MaterialInstanceConstant, parameter_name: unreal.Name, value) -> bool:
       # Cambiar el parámetro vectorial de la instancia de material
       success = unreal.MaterialEditingLibrary.set_material_instance_vector_parameter_value(
           instance=material_instance,
           parameter_name=parameter_name,
           value=value
       )
       if success:
           # Guardar el asset después de modificarlo
           unreal.EditorAssetLibrary.save_loaded_asset(material_instance)
       return success
   ```

3. **Cargar la Instancia de Material y Definir el Parámetro**
   ```python
   material_instance = unreal.EditorAssetLibrary.load_asset("/Game/StarterContent/Materials/example_ins.example_ins'")
   parameter_name = unreal.Name("BaseColor")
   value = unreal.LinearColor(1.0, 0.0, 0.0, 1.0)  # Rojo
   ```

4. **Llamar a la Función y Verificar el Resultado**
   ```python
   success = set_material_vector(material_instance, parameter_name, value)
   if success:
       print("Parámetro vectorial establecido y guardado correctamente.")
   else:
       print("Error al establecer el parámetro vectorial.")
   ```

#### Explicación

- **Importar Librerías**: Se importan las librerías necesarias de Unreal Engine.
- **Función `set_material_vector`**: 
  - Cambia el valor del parámetro vectorial en la instancia de material.
  - Guarda el material si la operación de cambio es exitosa.
  - Devuelve `True` si la operación se completa correctamente y `False` en caso contrario.
- **Cargar Material y Parámetro**: Carga la instancia de material y define el nombre del parámetro y el nuevo valor vectorial.
- **Verificar y Mostrar Resultado**: Llama a la función `set_material_vector` y muestra si la operación fue exitosa.

#### Referencias

Para más detalles, consulta la [documentación oficial de Unreal Engine sobre scripting en Python](https://docs.unrealengine.com/4.27/en-US/PythonAPI/class/EditorAssetLibrary.html).