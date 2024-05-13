
get_editor.property
set_editor.property

Son dos funciones que podemops usar para obtener y setear valores en el editor para assets o outliners, estas funciones suelen servir para proposito general, pero no siempre podremos acceder
a todas las propiedades que deseamos.

Para ello necesitaremos usar otro tipo de acceso a estas propiedades.

En este caso,  intentaremos acceder a una instancia de material.

Crearemos la instancia de un material (boton derecho create instance)

A continuacion comenzamos con el script para cambiar la propiedad emissive 01 de la instancia.

```python
#Cargamos librerias de Asset y Materiales
EditorAssetLibrary = unreal.EditorAssetLibrary()
MaterialEditingLibrary = unreal.MaterialEditingLibrary()

#Cargamos la instancia
instance = unreal.EditorAssetLibrary.load_asset("/Game/StarterContent/Materials/example_ins")

#Podemos hacer un print para ver que ha cargado

print(MaterialEditingLibrary.get_vector_parameter_names(instance))
#LOG: ["Emissive color 01", "Emissive color 02"]
#Como vemos nos devuelve una lista de dos elementos [!] Con espacios [!]

#A continuacion ejecutamos la sentencia para cambiar la propiedad "Emissive color 01" de tipo vector3 a los valores deseados
MaterialEditingLibrary.set_material_instance_vector_parameter_value(instance=instance, parameter_name="Emissive color 01", value=[0.1, 0.2, 0.3, 0.4])

```

Tras ejecutar el script podremos ver que la instancia ha cambiado los valores RGB + A

![[Pasted image 20240513185624.png]]