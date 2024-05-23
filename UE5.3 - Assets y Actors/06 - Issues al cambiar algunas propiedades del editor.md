No todas las propiedades cambiadas de forma automática mediante el metodo standard pueden funcionar de la manera esperada debido al sistema de notificacion de cambios de UE.

El sistema de notificacion se compone de una serie de metodos en UE que son llamadas una vez se realiza un cambio en el editor o de forma programatica para refrescar y cambiar aquellos otros valores que deban hacerlo debido al cambio.

En este caso usaremos una par de texturas (diffuse).

A la primera le cambiaremos de forma manual  el valor de Color Space situado en la seccion Texture -> Advanced.
Cambiamos ColorSpace a sRGB para probarlo.

![[Pasted image 20240513190638.png]]

Ahora, haremos lo mismo con la segunda textura, pero esta vez, mediante codigo:

```python
#Importamos EditorAssetLibrary
import unreal
EAL = unreal.EditorAssetLibrary()
#Cargamos la textura
asset = EAL.load_asset("/Game/StarterContent/prueba/T_Brick_Clay_New_D1")

#Camambiamos el ColorSpace mediante el seteo de una property

asset.source_color_settings.color_space = unreal.TextureColorSpace.TCS_S_RGB
#Nos acordamos de guardar el asset
EAL.save_loaded_asset(asset)
```

Tras ejecutar nuestro codigo, observaremos que todo parece haber ido bien, y de echo si miramos el ColorSpace de nuestra segunda textura, parece haber sido cambiado de forma correcta.
![[Pasted image 20240513192116.png]]


Sin embargo si entramos a la textura, la veremos negra, por lo que hay algo que no ha ido bien.

![[Pasted image 20240513192419.png]]

Lo que ocurre es que a pesar de que hemos cambiado bien la propiedad, la clase set_property no ha llamado al sistema de notificacion de cambios de Unreal, dejando sin actualizar los canales RGB + W que aparecen debajo de Color Space.

Si lo comparamos con el cambio que hicimos a la primera textura de forma manual, veremos que estos si se han actualizado, ahi esta la diferencia, y el error que tenemos.

![[Pasted image 20240513192634.png]]


Podemos pensar que simplemente cambiando estos valores a los deseados para el ColorSpace lo tendriamos hecho, pero no es asi, estos valores son computados en base a parametros de la propia instancia, por lo que la solucion sera encontrar una forma de cambiar esta propiedad que realmente llame al sistema de notificacion.


Probaremos ahora a cambiarlo mediante el metodo get_property:

```python

#Cargamos el asset (doy por supouesto que ya se ha cargado EAL)
asset = EAL.load_asset("/Game/StarterContent/prueba/T_Brick_Clay_New_D1")

asset.get_editor_property("source_color_settings").color_space = unreal.TextureColorSpace.TCS_S_RGB

```

Veremos tras ejecutar el codigo que el resultado es el mismo, y ahora veremos porque ocurre esto.

![[Pasted image 20240513194006.png]]

El metodo set_property definido en unreal, tiene como parmametro "notify_mode:" y por defecto es DEFAULT.
Es decir, no esta forzando la llamada al sistema de notificacion.

PropertyAccessChangeNotifyMode.DEFAULT

Si llamamos a este metodo cambiandolo por ALWAYS, veremos que el problema esta resuelto.

PropertyAccessChangeNotifyMode.ALWAYS


Si entramos a la clase PropertyAcessChange...
Veremos que tiene distintos modos:
![[Pasted image 20240513194300.png]]


```python
#Cargamos el asset
asset = EAL.load_asset("/Game/StarterContent/prueba/T_Brick_Clay_New_D1")

#Usamos el set_property definiendo el modo a always

asset.source_color_settings.set_editor_property("color_space", unreal.TextureColorSpace.TCS_S_RGB, unreal.PropertyAccessChangeNotifyMode.ALWAYS)
```


Tras ejecutar el codigo comprobaremos que la textura ha sido modificada ahora de forma correcta, tanto a nivel de ColorSpace como de subsettings, y vuelve a ser visible.

![[Pasted image 20240513194633.png]]