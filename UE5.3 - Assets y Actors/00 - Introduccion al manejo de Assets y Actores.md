
En esta documentacion se explica el workflow standard para el tratamiento de Assets y Actores en UE5.3, así como la automatización programática de tareas que puedan surgir durante el desarrollo de producto.

El texto actual define de forma rapida la forma standard de acceder a Assets y cambiar sus propiedades, estas formas pueden cambiar en base a la version de UE que se use.

--

A continuacion se expone la forma standard de acceso, que estará mas detallada en  los siguientes puntos.


#### Paso 1: Importar las Bibliotecas Necesarias

Lo primero que debes hacer es importar las bibliotecas  relevantes, como `unreal`.


```python
import unreal
```
`


Utiliza funciones de la biblioteca de Unreal para acceder a los activos que necesitas modificar. En este caso, se utilizan funciones de `EditorAssetLibrary` para listar los activos en un directorio específico.


```python
AssetLibrary = unreal.EditorAssetLibrary() asset_path_lst = AssetLibrary.list_assets("/Game/StarterContent/Textures/", recursive=False)`
```
#### Paso 3: Cargar el Actor o Asset

Para acceder a las propiedades de un actor o activo, primero necesitas cargarlo desde el contenido del proyecto. En este ejemplo, las texturas se cargan utilizando 
```python
AssetLibrary.load_asset()
```



```python
package_name = asset_path_lst[0].split('.')[0]  # Obtener nombre sin exntesion
extensión texture = AssetLibrary.load_asset(package_name)  # Cargar la textura
```
#### Paso 4: Verificar el Tipo de Actor/Asset

Asegúrate de que el actor o activo cargado sea del tipo que esperas para evitar errores durante la modificación. En este ejemplo, comprobamos que el activo es una `Texture2D`.


```python
if not isinstance(texture, unreal.Texture2D):     print("El activo no es una textura válida")     return
```
#### Paso 5: Obtener la Propiedad Actual

Usa `get_editor_property` para obtener el valor actual de la propiedad que quieres modificar.

python

Copy code

`current_compression = texture.get_editor_property("compression_settings") print(f"Compresión actual: {current_compression}")`

#### Paso 6: Modificar la Propiedad

Usa `set_editor_property` para establecer un nuevo valor. Ten en cuenta que los valores deben ser compatibles con el tipo de dato de la propiedad.

python

Copy code

`nuevo_valor = unreal.TextureCompressionSettings.TC_NORMALMAP texture.set_editor_property(name="compression_settings", value=nuevo_valor) print(f"Compresión modificada: {nuevo_valor}")`

### Consideraciones Adicionales

- **Permisos y Escritura**: Asegúrate de que el proyecto no esté en modo de solo lectura. Los cambios requieren permisos de escritura.
- **Guardar Cambios**: Si es necesario, guarda los cambios a través del menú de Unreal o con una función de guardado automática.
