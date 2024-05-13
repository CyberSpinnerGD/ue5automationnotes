```python

Con isinstance podemos comprobar si un asset es de un tipo determinado.
SACA POR PANTALLA TRUE O FALSE EN BASE A SI ESE ASSET ES DE ESE TIPO

# Verificación para un Static Mesh
print(isinstance(example_asset, unreal.StaticMesh))

# Verificación para un Skeletal Mesh
print(isinstance(example_asset, unreal.SkeletalMesh))

# Verificación para un Material
print(isinstance(example_asset, unreal.Material))

# Verificación para una instancia de material
print(isinstance(example_asset, unreal.MaterialInstance))

# Verificación para una textura 2D
print(isinstance(example_asset, unreal.Texture2D))

# Verificación para un sonido
print(isinstance(example_asset, unreal.SoundWave))

# Verificación para un sistema de partículas
print(isinstance(example_asset, unreal.ParticleSystem))

# Verificación para un Blueprint
print(isinstance(example_asset, unreal.Blueprint))

# Verificación para un nivel o mundo
print(isinstance(example_asset, unreal.World))

# Verificación para una cámara
print(isinstance(example_asset, unreal.CameraComponent))

# Verificación para una luz direccional
print(isinstance(example_asset, unreal.DirectionalLight))

# Verificación para una luz puntual
print(isinstance(example_asset, unreal.PointLight))
