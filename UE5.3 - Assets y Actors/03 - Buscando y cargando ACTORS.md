Un Actor es un Asset definido en la escena, por lo que ya cuenta con propiedades propias en el editor que pueden ser cambiadas, y aparece en el OUTLINER.



```python
#Metodo INCORRECTO Deprecado a partir de >UE5.3
unreal.EditorActorSubsystem().get_all_level_actors()

#Metodo CORRECTO para >UE5.3

unreal.get_editor_subsystem(unreal.EditorActorSubsystem)

#Para facilitar el trabo lo asignamos a una variable

actor_subsystem = unreal.get_editor_subsystem(unreal.EditorActorSubsystem)

# Obtener todos los actores del nivel en un array

all_actors = actor_subsystem.get_all_level_actors()

print(all_actors) #imprimimos el array

```