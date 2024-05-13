python````

```python
import unreal

# Obtener el subsistema del actor del editor
actor_subsystem = unreal.get_editor_subsystem(unreal.EditorActorSubsystem)

# Obtener todos los actores en el nivel actual
all_actors = actor_subsystem.get_all_level_actors()

# Listar actores de varios tipos específicos
print("# Actores de tipo SkyAtmosphere")
for actor in all_actors:
    if isinstance(actor, unreal.SkyAtmosphere):
        print(actor)

print("\n# Actores de tipo PointLight")
for actor in all_actors:
    if isinstance(actor, unreal.PointLight):
        print(actor)

print("\n# Actores de tipo DirectionalLight")
for actor in all_actors:
    if isinstance(actor, unreal.DirectionalLight):
        print(actor)

print("\n# Actores de tipo StaticMeshActor")
for actor in all_actors:
    if isinstance(actor, unreal.StaticMeshActor):
        print(actor)

print("\n# Actores de tipo SkeletalMeshActor")
for actor in all_actors:
    if isinstance(actor, unreal.SkeletalMeshActor):
        print(actor)

print("\n# Actores de tipo CameraActor")
for actor in all_actors:
    if isinstance(actor, unreal.CameraActor):
        print(actor)

print("\n# Actores de tipo ParticleSystemActor")
for actor in all_actors:
    if isinstance(actor, unreal.ParticleSystemActor):
        print(actor)

print("\n# Actores de tipo SoundCue")
for actor in all_actors:
    if isinstance(actor, unreal.SoundCue):
        print(actor)

print("\n# Actores de tipo BlueprintGeneratedClass")
for actor in all_actors:
    if isinstance(actor, unreal.BlueprintGeneratedClass):
        print(actor)

#SELECCIONANDO LOS ASSETS desde el EDITOR
#Con este metodo podemos primero seleccionar en el Outliner los actores que queremos cargar, despues llamar a la funcion e imprimirlos

selected_actors = actor_subsystem.get_selected_level_actors()
print(selected_actors)