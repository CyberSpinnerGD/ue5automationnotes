Cuando se importa un **FBX**, Unreal hace un primer broadcast para `On_Asset_Post_Import` la primera vez y el resto de importaciones el broadcast se hace SOLO contra `On_AssetReimport`. 

Sin embargo, cuando el activo que se importa es una TEXTURA, se llama a `On_Asset_Post_Import` tanto durante la importación como la reimportación.

Descubrí esto mientras exploraba el código CPP de las fábricas ya que me estoy volviendo loco.

**En resumen:**

**Para FBX:**

- **_BroadcastAssetPostImport_** se ejecuta solo durante la primera importación.
- **_BroadcastAssetReimport_** se ejecuta durante la reimportación.

[Ver código de FBXFactory](https://github.com/EpicGames/UnrealEngine/blob/16dc333db3d6439c7f2886cf89db8907846c0e8a/Engine/Source/Editor/UnrealEd/Private/Fbx/FbxFactory.cpp)

**Para Texturas:**

- **_BroadcastAssetPostImport_** se ejecuta tanto durante la importación como la reimportación.
