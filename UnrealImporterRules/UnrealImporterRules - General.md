

1. **Propósito del Plugin**
   - **Automatización de Importación:** Permite automatizar tareas durante la importación de archivos, como convertir texturas en sprites, establecer propiedades predeterminadas en materiales, o mover archivos a carpetas específicas basadas en convenciones de nombres.

2. **Enfoques para Automatización**
   - **Soluciones Externas:** Puedes usar soluciones externas desarrolladas por otros o descargadas de GitHub.
   - **Callbacks Manuales:** También puedes registrar callbacks manualmente en el subsistema de importación de Unreal.

3. **Uso del Plugin Unreal Importer Rules**
   - **Facilidad de Uso:** Este plugin, creado por Ryan Dowling-Soka, facilita la creación de reglas de importación.
   - **Disponibilidad:** El plugin está disponible en GitHub bajo la licencia MIT, lo que permite su uso y modificación en cualquier proyecto.

4. **Cómo Funciona el Plugin**
   - **Registro de Reglas:** Permite registrar reglas de importación específicas para cada clase de asset.
   - **Consultas y Acciones:** Cada regla tiene consultas (queries) que deben cumplirse para activar ciertas acciones (actions).
   - **Consultas:** Son clases simples con un método `test` que devuelve `true` o `false`.
   - **Acciones:** Heredan de una clase abstracta `ImportActionBase` y requieren implementar un método `apply`.

5. **Implementación de una Regla de Importación**
   - **Definición de Consultas:** Crear consultas para verificar condiciones específicas de los archivos importados.
   - **Definición de Acciones:** Implementar acciones que se ejecutarán si las consultas devuelven `true`.

6. **Ejemplo Práctico**
   - **Crear Mesh en Blender:** Crear un mesh con un atributo personalizado en Blender.
   - **Instalar el Plugin:** Descargar e instalar el plugin desde GitHub.
   - **Registrar Reglas:** Registrar reglas en el archivo `__init__.py` del plugin para que se ejecuten al iniciar Unreal Engine.

### Explicación Simplificada

1. **Propósito del Plugin**
   - **Automatización:** El plugin Unreal Importer Rules automatiza tareas al importar assets, lo que ahorra tiempo y esfuerzo.

2. **Enfoques**
   - Puedes usar soluciones externas o registrar tus propios callbacks manualmente.

3. **Uso del Plugin**
   - **Fácil de Usar:** El plugin facilita la creación de reglas de importación y es compatible con Python y C++.
   - **Disponible en GitHub:** Puedes descargar y modificar el plugin según tus necesidades.

4. **Funcionamiento**
   - **Registro de Reglas:** Define reglas específicas para cada tipo de asset.
   - **Consultas y Acciones:** Usa consultas para verificar condiciones y acciones para realizar tareas si las condiciones se cumplen.

5. **Implementación**
   - **Crear Consultas:** Define condiciones para los archivos importados.
   - **Crear Acciones:** Define lo que se debe hacer cuando las condiciones se cumplen.



