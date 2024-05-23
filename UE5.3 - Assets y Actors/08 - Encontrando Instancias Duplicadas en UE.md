
Es común tener en escena por equivocación instancias de un mismo asset duplicadas, por ejemplo, varios modelos 3D exactamente iguales cuando solo debería haber uno.

Para solucionar esto, podemos automatizar el proceso, sin embargo es importance recalcar que no buscaremos las instancias por medio del nombre de la misma, si no por el nombre del asset a partir del cual se ha creado.


Cuando usamos actor.get_fname() en unreal, al menos en la version en la que trabajo 5.3.2 lo que devuelve es lo siguiente:

StaticMeshActor_UAID_D843AE554A22C9F501_1254303261


```python
import unreal  

#Cargamos EAS

EAS = unreal.get_editor_subsystem(unreal.EditorActorSubsystem)

#Cargamos Actores

actors = EAS.get_all_level_actors()

  

for actor in actors:

    actor_name = actor.get_fname()

    print(f"Actor encontrado:")

    print(f"{actor_name}")
```