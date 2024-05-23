En UE podemos trabajar a nivel de Asset

Un  asset es cualquier archivo que se encuentre en el ContentDrawer, y se trabaja con el a nivel de file.



Para cargar la libreria de Assets la meteremos primero en una variable para evitar que la linea sea muy larga al trabajar con ella.
python


```python
# CARGAR AssetLibrary
EditorAssetLibrary = unreal.EditorAssetLibrary()


#Una vez hecho esto, podemos listar los Assets de la siguiente forma (siguiendo #rutas definidas en el ContentDrawer)


#LISTAR ASSETS POR PATH

assets = EditorAssetLibrary.list_assets("/Game/StarterContent/Architecture")

#Esto nos devolvera un array con los distintos paths de los assets encontrados en la ruta definida, para seleccionar una especifico, simplemento lo cargamos definiendo el indice en una nueva variable.

example_asset_path = assets[0]

#Para cargar el asset establecido ahora en la variable:

example_asset = EditorAssetLibrary.load_asset(example_asset_path)



```



