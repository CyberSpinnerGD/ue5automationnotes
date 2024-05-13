

En Unreal Engine, las propiedades de los actores pueden ser accedidas y cambiadas utilizando Python. Aquí se muestra un ejemplo sobre cómo cambiar la propiedad `compression_settings` de una textura. Sin embargo, este procedimiento puede aplicarse a cualquier propiedad de un actor (consultar documentacion de UE5).

Obtener la Propiedad Actual

Usa `get_editor_property` para obtener el valor actual de la propiedad que quieres modificar.

```python
current_compression = texture.get_editor_property("compression_settings") print(f"Compresión actual: {current_compression}")

#Modificar la Propiedad

#Usa `set_editor_property` para establecer un nuevo valor. Ten en cuenta que los #valores deben ser compatibles con el tipo de dato de la propiedad.

nuevo_valor = unreal.TextureCompressionSettings.TC_NORMALMAP texture.set_editor_property(name="compression_settings", value=nuevo_valor) print(f"Compresión modificada: {nuevo_valor}")
