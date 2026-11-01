# Ejercicios del participante

## Cómo seguir la práctica

Esta es la guía completa de la práctica. Primero completa las instalaciones y la autenticación de la [preparación](01%20-%20preparacion.md); después realiza la sección «Antes de la sesión» de esta página. Durante el taller, sigue los ejercicios 1 a 6 en orden y termina con el cierre. Trabaja en el repositorio nuevo de práctica, no en el clon del material del taller. Todos los tiempos corresponden al [temario](00%20-%20temario.md).

| Momento | Qué haces tú | Qué hace Squad | Antes de avanzar |
| :--- | :--- | :--- | :--- |
| Antes de la sesión | Instalas herramientas, te autenticas y preparas el proyecto con los pasos de esta página | El coordinador queda configurado; no recibe encargos ni forma el equipo | Repositorio preparado e inicio de sesión comprobado, o alternativa acordada |
| Ejercicio 1 | Seleccionas Squad y apruebas los roles | Propone y guarda el equipo y su reparto | Nueve especialistas con responsabilidades verificables |
| Ejercicio 2 | Das el contexto de Python o .NET y entregas el contrato común | Redacta la especificación y propone dependencias | Lees y apruebas la especificación antes de implementar |
| Ejercicio 3 | Autorizas la implementación y ejecutas los comandos de Python o .NET | Delega código, pruebas y documentación | Aplicación ejecutada y número de pruebas registrado |
| Ejercicio 4 | Contrastas los casos de aceptación y apruebas reparaciones concretas | Revisa y corrige solo lo autorizado | Caso reparado y suite repetidos, o revisión sin hallazgos |
| Ejercicio 5 | Cierras la conversación y abres otra interfaz | Recupera decisiones desde los archivos | Compruebas una decisión persistente |
| Ejercicio 6 | Configuras dos modelos distintos en CLI y contrastas las evidencias | Lanza los especialistas del plan aprobado, si la interfaz lo permite | Distingues modelos guardados, solicitados y reportados, y restauras preferencias |
| Cierre | Revisas cambios y anotas evidencias | No publica ni hace commit | Puedes explicar qué hicieron los agentes y qué revisaste tú |

En cada paso con alternativas, ejecuta solo el bloque de Python o de .NET que corresponda al proyecto con el que trabajas y a tu *entorno de shell*. Las acciones comunes, como configurar Squad, aparecen una sola vez. Si decides practicar ambos lenguajes, utiliza sus repositorios separados: no ejecutes comandos de .NET dentro de la práctica Python ni al contrario.

La explicación está en español. Cada mensaje para copiar en Squad se ofrece en español y en inglés: elige una sola versión, no envíes ambas. Las dos piden lo mismo; el idioma de la conversación no cambia la política del proyecto. Los *charters* y las instrucciones generadas deben estar en inglés; la documentación de la aplicación y sus mensajes de consola estarán en español.

Dirige tus peticiones a Squad con objetivos, entregables y límites, sin indicar qué miembro debe realizar cada acción. El coordinador debe decidir el reparto usando los *charters* y el *routing* del equipo, ordenar las dependencias y explicar sus delegaciones. Tú apruebas el alcance y verificas las ejecuciones reales; no repartes manualmente las tareas entre los especialistas (a menos que sea estrictamente necesario).

## Antes de la sesión: preparar el proyecto

Estos tres pasos se hacen fuera de los 105 minutos, después de instalar las herramientas comunes y autenticarte. Hazlos tú en la terminal; todavía no abras una conversación con Squad ni encargues la aplicación a los agentes.

### Paso 1: verificar el lenguaje elegido

Sitúate fuera del clon del material y elige la alternativa de tu proyecto. Mantén el mismo sistema durante toda la práctica; si utilizas WSL (Windows Subsystem for Linux), instala y ejecuta las herramientas dentro de Linux.

#### Python: comprobar el intérprete

Utilizamos Python 3.12 como versión menor de referencia. La aplicación utilizará solo la biblioteca estándar: argumentos de consola, JSON y `unittest`. No necesitas FastAPI, servicios externos ni paquetes Python adicionales.

Python 3.12 sigue recibiendo correcciones de seguridad, pero ya no publica nuevos instaladores binarios de mantenimiento. Para Windows y macOS, Python 3.12.10 fue la última publicación con esos instaladores; usa una distribución de 3.12 con parches de seguridad si está disponible para tu plataforma. Este es un entorno educativo local, no una recomendación de runtime para producción.

Instala Python desde los [distribuidores oficiales](https://www.python.org/downloads/) o el gestor de tu sistema. En Linux o WSL puede ser necesario instalar el paquete de soporte de `venv` para Python 3.12. No sustituyas el Python del sistema. Si tu equipo no puede disponer de 3.12, acuerda con el instructor otra versión soportada y registra la diferencia.

En PowerShell 7, comprueba el intérprete:

```powershell
py -3.12 --version
```

En Bash:

```bash
python3.12 --version
```

Antes de avanzar: debe aparecer Python 3.12. Si el comando falta o muestra otra versión, resuelve la instalación antes de crear el entorno.

#### C# con .NET: comprobar el SDK

Instala el SDK de .NET 10, no únicamente el runtime, desde la [descarga oficial](https://dotnet.microsoft.com/download/dotnet/10.0). .NET 10 es LTS. El material del repositorio fija el SDK 10.0.402 como referencia; la práctica se crea fuera del clon y puede utilizar un SDK 10.0 actualizado, dejando registrada su versión.

Utilizaremos una aplicación de consola, `System.Text.Json` y pruebas xUnit. Descarga los paquetes de pruebas en el paso 2, antes de los 105 minutos. No necesitas ASP.NET Core, Azure, una base de datos ni el paquete Squad.Agents.AI: Squad es la herramienta de desarrollo, no una dependencia de la aplicación.

En PowerShell 7 o Bash, comprueba los SDK y el que usaría esa terminal:

```text
dotnet --list-sdks
dotnet --version
```

Antes de avanzar: `dotnet --version` debe indicar 10.0. Si muestra otra versión mayor, elige un SDK 10.0 mediante `global.json` con ayuda del instructor y vuelve a comprobarlo. No copies el SDK del clon si no lo tienes instalado.

### Paso 2: crear el repositorio y preparar el entorno

Sitúate en una carpeta donde quieras guardar la práctica, fuera del clon del material. Ejecuta solo la alternativa elegida. Si esa carpeta ya existe de una preparación anterior, entra en ella y comprueba su entorno; no repitas la creación ni borres sus archivos.

#### Python: crear el entorno virtual

En PowerShell 7, crea el repositorio y un intérprete aislado para el proyecto:

```powershell
mkdir study-tasks-python
cd study-tasks-python
git init -b main
py -3.12 -m venv .venv
.venv\Scripts\python.exe --version
```

En Bash:

```bash
mkdir study-tasks-python
cd study-tasks-python
git init
python3.12 -m venv .venv
.venv/bin/python --version
```

El entorno virtual evita mezclar el proyecto con el Python global. Usaremos su ejecutable directamente, sin cambiar políticas para activar scripts.

Antes de avanzar: estás en la raíz `study-tasks-python`, Git está inicializado y el ejecutable de `.venv` responde con 3.12. Aún no hay aplicación ni pruebas: es el resultado esperado.

#### C# con .NET: crear los proyectos

En PowerShell 7 o Bash, crea el repositorio y confirma el SDK desde su raíz:

```text
mkdir study-tasks-dotnet
cd study-tasks-dotnet
git init
dotnet --version
```

Si el SDK no es 10.0, detente y resuelve su selección. Desde esa misma raíz, crea los dos proyectos, conecta las pruebas con la aplicación y descarga sus dependencias:

```text
dotnet new console --name StudyTasks --output src/StudyTasks --framework net10.0
dotnet new xunit --name StudyTasks.Tests --output tests/StudyTasks.Tests --framework net10.0
dotnet add tests/StudyTasks.Tests/StudyTasks.Tests.csproj reference src/StudyTasks/StudyTasks.csproj
dotnet restore tests/StudyTasks.Tests/StudyTasks.Tests.csproj
dotnet build src/StudyTasks/StudyTasks.csproj
dotnet test tests/StudyTasks.Tests/StudyTasks.Tests.csproj
```

No cambies de carpeta al crear los proyectos: `src/` y `tests/` deben quedar dentro de la raíz de práctica. La consola contiene el saludo de la plantilla y la prueba inicial solo comprueba el entorno. No es la solución del taller: Squad deberá sustituir el saludo y la prueba vacía por funcionalidad y pruebas reales.

Antes de avanzar: estás en la raíz `study-tasks-dotnet`, ambos proyectos existen, la compilación y las pruebas de plantilla terminan sin errores y las dependencias están descargadas.

### Paso 3: inicializar Squad y abrir el proyecto

Este paso es común a Python y .NET. Sin cambiar de carpeta, ejecuta estos comandos tú en PowerShell 7 o Bash:

```text
squad init --state-backend local --no-workflows
squad doctor
code .
```

`squad init` prepara la configuración local y el agente coordinador, sin añadir flujos de GitHub Actions. No implementa la aplicación ni sustituye la conversación donde definirás el equipo. El comando `squad doctor` muestra el estado de la instalación; revisa sus avisos antes de continuar.

Si la inicialización pregunta `Add @copilot as an autonomous team member? [Y/n]`, responde `n`: esta práctica mantiene supervisión humana y no incorpora ese miembro autónomo.

Si `code` no está en PATH, abre la carpeta de práctica desde VS Code. En WSL utiliza la ventana conectada a WSL, no otra ventana de Windows. Debes ver `.squad` y `.github/agents/squad.agent.md`, además de `.venv` en Python o `src` y `tests` en .NET. La terminal integrada debe estar en la raíz de la práctica.

#### Configurar las herramientas MCP

MCP (*Model Context Protocol*) conecta GitHub Copilot con servidores que ofrecen herramientas y acceso a datos. Squad decide qué especialistas trabajan; MCP aporta capacidades que esos agentes pueden utilizar si su sesión las tiene disponibles. Escribir el nombre de un servidor en un mensaje no lo instala ni le concede permisos.

En Squad 1.1.0, `squad init` genera una entrada `squad_state` en `.mcp.json`, en la raíz del proyecto. El **`squad_state` es el nombre del servidor MCP, no una herramienta única**. El comando que lo ejecuta es `squad state-mcp`; el cliente lo inicia y se comunica con él mediante entrada y salida estándar (`stdio`). No necesitas dejarlo ejecutándose en otra terminal.

Este servidor permite consultar y mantener el estado persistente de Squad: decisiones, historiales de agentes y registros de trabajo. Con `--state-backend local`, el estado se conserva en `.squad/`.

| Herramienta del servidor | Para qué sirve |
| :--- | :--- |
| `squad_state_read` | Leer una entrada de estado |
| `squad_state_list` | Enumerar entradas de estado |
| `squad_state_health` | Consultar la salud del almacenamiento de estado |
| `squad_decide` | Registrar una decisión mediante el mecanismo de Squad |
| `squad_state_write` | Escribir estado mutable permitido |
| `squad_state_append` | Añadir contenido a estado mutable permitido |
| `squad_state_delete` | Eliminar una entrada de estado mutable permitida |

**En VS Code:**

1. Abre `.mcp.json` y revisa la entrada `squad_state`: debe apuntar a la versión 1.1.0 instalada o a su distribución standalone, no a `@insider` ni a otra versión sin aprobación.
2. Comprueba si el editor descubre esa configuración. Si no aparece, ejecuta **MCP: Add Server** desde la paleta y elige **Command (stdio)**. Para la instalación npm del taller, introduce `npx -y @bradygaster/squad-cli@1.1.0 state-mcp`, utiliza el identificador `squad_state` y guarda la configuración en el ámbito del proyecto. Si usas standalone, utiliza el ejecutable instalado de Squad con el argumento `state-mcp`, no `npx`.
3. Si el editor ofrece el formato de VS Code, la configuración se guarda en `.vscode/mcp.json` bajo `servers`; el formato portable de `.mcp.json` utiliza `mcpServers`. No copies un archivo completo sobre el otro ni sobrescribas servidores existentes. Evita activar dos conexiones `squad_state` para la misma sesión.
4. Revisa los avisos de confianza y arranca el servidor desde la gestión de MCP del editor. Comprueba que aparecen sus herramientas; si falla, consulta su salida y verifica el comando, el runtime y la carpeta de trabajo de la práctica.
5. Con Squad seleccionado, revisa las herramientas disponibles en el chat mediante **Configure Tools** o **Chat: Open Customizations > Tools**, según la versión. El servidor debe estar disponible para ese agente, no solo instalado en el editor. Mantén la aprobación por operación; no habilites permisos globales.

La primera conexión mediante `npx` puede descargar el paquete: complétala antes del taller. En WSL, tanto el runtime como el servidor deben ejecutarse dentro de WSL. Si una política de tu organización impide usar MCP, avisa al instructor; no intentes eludirla.

**En Copilot CLI:** conserva la entrada generada en `.mcp.json`. Durante el ejercicio 5 iniciarás la sesión desde la raíz de la práctica con esa configuración explícita:

```text
copilot --agent squad --additional-mcp-config "@.mcp.json"
```

El argumento `@.mcp.json` identifica un archivo de configuración; no es un marcador que debas reemplazar. Conserva las comillas: funcionan en PowerShell y Bash y evitan que PowerShell interprete `@` como sintaxis especial. Revisa la confianza del proyecto y las autorizaciones solicitadas. No añadas `--yolo` ni `--allow-all-tools`. Una conexión configurada en VS Code no demuestra que también esté conectada en CLI.

Otros servidores MCP pueden aportar documentación, consultas a GitHub o acceso a sistemas del proyecto. Configura solo los que necesites, con instrucciones de su proveedor y permisos mínimos. No son obligatorios para esta práctica local: `squad_state` no necesita tokens de servicios externos. No pegues secretos en el chat ni los guardes en archivos versionados.

Referencias: [generación de `.mcp.json` en Squad 1.1.0](https://github.com/bradygaster/squad/blob/v1.1.0/packages/squad-cli/src/cli/core/mcp-root.ts), [herramientas del servidor de estado](https://github.com/bradygaster/squad/blob/v1.1.0/packages/squad-cli/src/cli/commands/state-mcp.ts), [backends de estado](https://github.com/bradygaster/squad/blob/v1.1.0/docs/src/content/docs/features/state-backends.md) y [configuración MCP en VS Code](https://code.visualstudio.com/docs/agent-customization/mcp-servers).

Antes de avanzar: revisa la [lista de preparación](01%20-%20preparacion.md#lista-de-preparación) y detente. No necesitas enviar mensajes a Squad todavía. Durante el taller, continúa aquí con el ejercicio 1; el contexto técnico y la implementación vendrán después.

## Ejercicio 1: formar y ampliar el equipo

Tiempo: minutos 15-30, 15 minutos. Objetivo: tener cuatro arquetipos base y cinco adicionales con responsabilidades distintas.

Punto de partida: has completado los tres pasos de [preparación del proyecto](#antes-de-la-sesión-preparar-el-proyecto). El comando `squad init` preparó los archivos del coordinador; este ejercicio configura las personas y responsabilidades del equipo. No vuelvas a crear el repositorio ni a ejecutar la inicialización.

### Paso 1: seleccionar Squad

Desde la raíz de tu práctica, abre VS Code, muestra Copilot Chat y selecciona Squad en el selector de agentes. Si no aparece, comprueba que existe `.github/agents/squad.agent.md` y reinicia la sesión. **No basta seleccionar el modo Agent genérico**.

### Paso 2: proponer y aprobar el equipo

Esta es tu primera conversación con Squad en el taller. Envía el mensaje de formación para proponer el equipo. Si retomaste un proyecto que ya tenía miembros, conserva sus conocimientos y ajusta sus roles sin duplicarlos.

Versión en español:

```text
Estamos construyendo una aplicación local de tareas de estudio por consola
en un taller para principiantes.

Conserva los conocimientos de los miembros si ya existe un equipo.

Configura estos cuatro arquetipos base con charters distintos:
- Lead: contratos técnicos y revisión final.
- Backend: comportamiento de comandos y lógica de dominio.
- Frontend adaptado a la experiencia de consola: ayuda y mensajes en español.
- Tester: pruebas de aceptación y regresión.

Adicionalmente, añade cinco arquetipos de especialistas:
- Producto: alcance y criterios de aceptación.
- Persistencia: esquema JSON y lectura y escritura seguras.
- Seguridad: validación de entradas y revisión del manejo de datos.
- Documentación: guía de uso en español e índice de evidencias.
- Portabilidad: comprobación de comandos en PowerShell 7 y Bash.

Conserva el coordinador y los miembros operativos como Scribe o Ralph;
no los cuentes entre estos nueve especialistas.

Mantén los *charters* y las instrucciones en inglés. Propón nombres de héroes Marvel solo como identificadores de rol. Conserva los nueve roles y muestra la correspondencia real entre nombres y roles en lugar de inventar miembros.

Define los *charters* y el *routing* para que Squad pueda elegir automáticamente los especialistas adecuados a cada petición. No fijes un reparto de tareas de implementación todavía.

Propón primero el equipo, los límites de responsabilidad y el *routing*; después espera.

No instales paquetes, crees flujos de trabajo, hagas push o commit
ni inicies el modo de vigilancia.
```

Versión en inglés:

```text
We are building a local study task CLI in beginner workshop.

Preserve existing member knowledge if a team already exists.

Configure these four base archetypes with distinct charters:
- Lead: technical contracts and final review.
- Backend: command behavior and domain logic.
- Frontend adapted to console UX: help and Spanish messages.
- Tester: acceptance and regression tests.

Add five genuinely additional specialist archetypes:
- Product: scope and acceptance criteria.
- Persistence: JSON schema and safe read/write behavior.
- Security: input validation and data handling review.
- Documentation: Spanish usage guide and evidence index.
- Portability: PowerShell 7 and Bash command verification.

Keep the coordinator and operational members such as Scribe or Ralph;
do not count them among these nine specialists.

Keep charters and instructions in English. Propose Marvel hero names as role identifiers. Preserve the nine roles and show the actual name-to-role mapping instead of inventing members.

Define charters and routing so Squad can automatically select the appropriate specialists for each request. Do not preassign implementation tasks yet.

Propose the roster, ownership boundaries and routing first, then wait.

Do not install packages, create workflows, push, commit or start watch mode.
```

Lee la propuesta: deben aparecer nueve especialistas además de los miembros operativos. Confirma su creación cuando los roles sean correctos. Los nombres pueden variar; anota la correspondencia real con los roles. Los mensajes posteriores no necesitan nombres de miembros: Squad elegirá a quién delegar según el trabajo y los charters.

### Paso 3: comprobar los archivos del equipo

Abre el *roster*, el *routing* y el *charter* de al menos un arquetipo. Lo habitual es encontrarlos en `.squad/team.md`, `.squad/routing.md` y `.squad/agents/`.

Comprueba que sus responsabilidades son distintas y que el *routing* permite seleccionar especialistas según la petición. Un nombre en el chat no demuestra que un miembro exista ni que se haya ejecutado.

## Ejercicio 2: acordar contrato y límites

Tiempo: minutos 30-40, 10 minutos. Objetivo: que Python y .NET construyan el mismo comportamiento.

Punto de partida: el equipo del ejercicio 1 existe y sus roles están guardados. Primero envía el contexto técnico correspondiente a tu proyecto; después entrega el contrato común y pide el plan de trabajo. Ninguno de estos mensajes autoriza a implementar la aplicación todavía.

### Paso 1: dar el contexto técnico

En Copilot Chat con Squad seleccionado, elige Python o .NET y envía una sola versión del mensaje de esa alternativa. No envíes los contextos de ambos lenguajes al mismo proyecto. En principio, no debería generar nada, simplemente indicar que ha leído y entendido el contexto técnico. Esta información quedará en el histórico de la conversación para futuras acciones.

#### Python: enviar el contexto

Versión en español:

```text
No implementes ni modifiques código de la aplicación hasta que la especificación compartida esté completa y una persona la haya aprobado explícitamente.

Este proyecto utiliza Python 3.12 y solo la biblioteca estándar.

Usa `study_tasks.py` en la raíz como punto de entrada de la consola, un módulo `task_store.py` separado para la persistencia y pruebas unittest en `tests/`.

Usa el intérprete existente de `.venv`; nunca instales paquetes globalmente.

Mantén en inglés los identificadores, comentarios, instrucciones y charters.

Escribe en español los mensajes de consola y la documentación para usuarios.

Excluye `.venv/`, `__pycache__/` y `data/tasks.json` local de Git.

No excluyas `.squad/` ni la definición del agente coordinador.

No construyas una aplicación web, recursos en la nube ni flujos de CI.
```

Versión en inglés:

```text
Do not implement or modify application code until the shared specification is complete and explicitly approved by a human.

This project uses Python 3.12 and only the standard library.

Use a root-level study_tasks.py command entry point, a separate `task_store.py` persistence module, and unittest tests under `tests/`.

Use the existing `.venv` interpreter; never install packages globally.

Keep identifiers, comments, instructions and team charters in English.

Keep user-facing console messages and application documentation in Spanish.

Ignore `.venv/`, `__pycache__/`, and local `data/tasks.json` in Git.

Do not ignore `.squad/` or the coordinator definition.

Do not build a web app, cloud resources, or CI workflows.
```

#### C# con .NET: enviar el contexto

Versión en español:

```text
No implementes hasta que exista una especificación compartida aprobada explícitamente por una persona.

Este proyecto usa .NET 10 con C# y `System.Text.Json`.

Conserva el proyecto de consola en `src/StudyTasks` y el proyecto xUnit en `tests/StudyTasks.Tests`. Separa comandos, lógica de dominio y persistencia en `TaskStore` sin añadir proyectos adicionales.

Usa el SDK .NET 10 instalado. No añadas otro framework de destino.

Sustituye la prueba vacía generada por pruebas reales de aceptación.

Mantén en inglés los identificadores, comentarios, instrucciones y charters.

Escribe en español los mensajes de consola y la documentación para usuarios.

Excluye `bin/`, `obj/` y `data/tasks.json` local de Git.

No excluyas `.squad/` ni la definición del agente coordinador.

No construyas una aplicación web, recursos en la nube ni flujos de CI.
```

Versión en inglés:

```text
Do not implement until the shared specification is explicitly approved by a human.

This project uses .NET 10 with C# and System.Text.Json.

Keep the existing console project under src/StudyTasks and the xUnit
project under tests/StudyTasks.Tests. Separate command handling,
domain behavior and TaskStore persistence without adding more projects.

Use the installed .NET 10 SDK. Do not add a different target framework.

Replace the generated empty test with real acceptance tests.

Keep identifiers, comments, instructions and team charters in English.

Keep user-facing console messages and application documentation in Spanish.

Ignore bin/, obj/, and local data/tasks.json in Git.

Do not ignore .squad/ or the coordinator definition.

Do not build a web app, cloud resources, or CI workflows.
```

### Paso 2: compartir el contrato funcional común

Copia a Squad el contrato completo de esta sección, incluido el ejemplo JSON, y la tabla de casos de aceptación del [ejercicio 4](#ejercicio-4-revisar-fallar-y-corregir). Este contrato es el mismo para Python y .NET.

````markdown
Construimos un gestor personal de tareas de estudio, con un único proceso escritor. Se ejecuta desde la raíz de la práctica y guarda datos en `data/tasks.json`, relativa al directorio de trabajo. No acepta una ruta de datos arbitraria desde la consola; las pruebas pueden inyectar una ruta temporal a la capa de persistencia.

| Comando de la aplicación | Comportamiento |
| :--- | :--- |
| `--help` | Explica los comandos en español y no cambia datos |
| `add "Repasar agentes"` | Añade una tarea pendiente y muestra su ID |
| `list` | Lista todas las tareas ordenadas por ID, con título y estado |
| `complete 1` | Marca la tarea existente como completada |

Los comandos y propiedades de datos están en inglés; la salida visible está en español. No se exige texto literal idéntico entre lenguajes, pero sí la misma información, estado y código de salida.

Reglas obligatorias:

- Un almacén inexistente equivale a una lista vacía; `list` no debe crearlo
- Solo una operación de escritura válida crea el directorio y el archivo
- Los IDs son enteros positivos únicos; una tarea nueva usa el máximo existente más uno, o 1 si no hay tareas
- El título se recorta en los extremos y debe tener entre 1 y 120 caracteres; se cuentan puntos de código Unicode en ambos lenguajes, no bytes ni unidades UTF-16
- Se rechazan títulos formados solo por espacios; no se ejecuta su contenido como código
- Una tarea nueva tiene `completed` igual a `false`
- Completar una tarea ya completada es idempotente y devuelve éxito
- Los IDs no enteros, negativos, cero o inexistentes producen un error legible
- Una operación correcta devuelve código de salida 0; los errores devuelven un código distinto de 0
- Argumentos inválidos y errores no alteran el archivo de datos
- Un JSON mal formado o con esquema inválido produce error, sin sobrescribirlo ni reiniciarlo silenciosamente
- El archivo se guarda en UTF-8 y se valida antes de escribir; no se necesita soportar dos procesos escritores ni garantizar recuperación frente a cortes de alimentación
- No hay red, autenticación, telemetría, fechas, prioridades, borrado ni despliegue en la aplicación

El documento JSON es una lista de objetos con estas tres propiedades. Este ejemplo es un dato válido después de añadir una tarea a un almacén nuevo.

```json
[
  {
    "id": 1,
    "title": "Repasar agentes",
    "completed": false
  }
]
```

Al cargar, comprueba que la raíz sea una lista y que cada elemento tenga exactamente `id`, `title` y `completed` con sus tipos correctos, IDs únicos y títulos válidos ya recortados. Un booleano no es un ID entero válido, aunque Python permita tratarlo como un número. No conviertas cadenas a booleanos ni ignores entradas inválidas.
````

### Paso 3: repartir el trabajo y aprobar el contrato

Pide a Squad que convierta el contrato en un plan y elija el reparto según los *charters*, sin implementar todavía. Revisa su razonamiento y los límites, sin sustituirlos por asignaciones manuales a miembros concretos.

Versión en español:

```text
Usa el contrato completo que acabo de proporcionarte.

- Redacta docs/spec.md en español con criterios de aceptación, el contrato JSON exacto y la interfaz de persistencia.
- Propón la propiedad de los archivos y el orden de las dependencias.
- Revisa los límites previstos para datos y permisos.

Decide a qué especialistas delegar estos entregables según sus *charters*
y el *routing*. Explica qué responsabilidades justifican cada elección.
Si varios especialistas contribuyen al mismo documento, elige un único
propietario para consolidarlo sin ediciones simultáneas.

Pídeme que resuelva las ambigüedades. No escribas código de la aplicación aún.

Distingue los requisitos propuestos de las decisiones aprobadas.

Después de la aprobación humana, registra el contrato acordado y los límites humanos en las decisiones compartidas del equipo, en inglés. Identifica los archivos reales utilizados para esas decisiones.

Usa como máximo dos ejecuciones independientes de especialistas a la vez.

Espera mi aprobación antes de implementar; no hagas commit ni push.
```

Versión en inglés:

```text
Use the complete contract I just gave you.

- Write docs/spec.md in Spanish with acceptance criteria, the exact JSON contract and the persistence interface.
- Propose file ownership and dependency order.
- Review the planned data and permission boundaries.
- Propose file ownership and dependency order.
- Review the planned data and permission boundaries.

Choose which specialists receive these deliverables based on their *charters*
and *routing*. Explain which responsibilities justify each choice.
If multiple specialists contribute to the same document, select one owner
to consolidate it without concurrent edits.

Ask me to resolve ambiguities. Do not write application code yet.

Keep proposed requirements distinct from approved decisions.

After human approval, capture the agreed contract and human limits in shared team decisions, in English. Identify the actual files used for those decisions.

Use at most two independent specialist executions at once.

Wait for my approval before implementation; do not commit or push.
```

Si varios agentes necesitan editar la especificación, deben aportar comentarios y el propietario elegido por Squad debe consolidarla.

Lee el documento de especificación `docs/spec.md` verifica que cumpla con los criterios de aceptación y que refleje correctamente el contrato acordado. Si hay que modificar algo, tienes dos opciones:

1. Proponer cambios al Squad, a modo de **vibe coding**, y revisar nuevamente el resultado, o
2. Implementar directamente tu mismo las modificaciones necesarias sobre el documento.

> **IMPORTANTE**: Puede ocurrir, como pasa con los seres humanos, que los agentes tengan preguntas, dudas o necesiten aclaraciones antes de poder tomar decisiones correctas. Si te realizan preguntas, aprovecha la oportunidad para aclarar y resolver cualquier ambigüedad antes de continuar.

## Ejercicio 3: delegar la implementación

Tiempo: minutos 40-60, 20 minutos. Objetivo: una aplicación ejecutable y pruebas reales, con entregas repartidas.

### Paso 1: autorizar la implementación

Aprueba la especificación y encarga a Squad el resultado completo. No elijas los especialistas: observa cómo el coordinador selecciona miembros y ordena el trabajo según sus *charters* y las dependencias del plan.

Versión en español:

```text
Apruebo docs/spec.md para su implementación.

- Construye la aplicación con la persistencia, la lógica de dominio y los comandos acordados.
- Incluye ayuda, estados vacíos y mensajes de error en español.
- Escribe pruebas reales basadas en la especificación, usando directorios temporales y las interfaces acordadas, no supuestas.
- Escribe una guía de uso en español en docs/usage.md.
- Comprueba los comandos de ejecución y pruebas para PowerShell 7 y Bash; distingue los comandos realmente ejecutados de la sintaxis revisada para otro sistema operativo.

Selecciona y delega automáticamente el trabajo a los especialistas apropiados
según sus charters y el routing. Coordina el orden de las dependencias y elige
un único propietario por archivo. No actives todos los miembros por defecto.
Informa de las delegaciones realmente ejecutadas, sus entregables y las
responsabilidades de los charters que justifican cada elección.
La revisión de los cambios terminados se realizará en el siguiente ejercicio.

Como máximo dos ejecuciones independientes a la vez; un escritor por archivo.

Produce solo código funcional: sin implementaciones vacías, resultados de pruebas ficticios ni bloques sin terminar.

No instales paquetes globales, crees recursos en la nube, flujos de trabajo ni una interfaz web.

No hagas commit o push ni reduzcas las restricciones de permisos de las herramientas. Comunícame los bloqueos.
```

Versión en inglés:

```text
I approve docs/spec.md for implementation.

- Build the application with the agreed persistence, domain behavior and commands.
- Include Spanish help, empty states and error messages.
- Write real tests based on the specification, using temporary directories and agreed interfaces rather than guessed ones.
- Write a Spanish usage guide in docs/usage.md.
- Check run and test commands for PowerShell 7 and Bash; distinguish commands actually executed from syntax reviewed for another operating system.

Automatically select and delegate work to the appropriate specialists based
on their charters and routing. Coordinate dependency order and choose one
owner per file. Do not activate every member by default.
Report the delegations actually executed, their deliverables and the charter
responsibilities that justify each choice.
Review of the completed changes will take place in the next exercise.

At most two independent executions at a time; one writer per file.

Produce working code only: no stubs, fake test results or unfinished blocks.

Do not install global packages, create cloud resources, workflows or web UI.

Do not commit, push or relax tool permissions. Report blockers to me.
```

Concede permisos solo para las operaciones que entiendas dentro de tu práctica. Observa qué miembros elige Squad, qué *charters* justifican la elección y qué archivos modifican. Si el coordinador hace todo sin delegar, pausa y pide que aplique el *routing* y seleccione los especialistas adecuados, sin nombrarlos tú. Si la interfaz no permite delegación real, registra la limitación en lugar de aceptar un diálogo simulado entre miembros.

### Paso 2: ejecutar la aplicación y las pruebas

Solo cuando Squad haya terminado la implementación, ejecuta tú la alternativa de tu proyecto en una terminal de su raíz, no en el chat. Cada invocación abre y cierra un proceso: volver a listar permite comprobar la persistencia. El ID 1 supone un almacén nuevo; si ya hay tareas, cambia ese argumento por el ID que devuelve `add`, sin borrar datos para forzar el número.

#### Python: ejecutar y probar

Comprueba en VS Code que existen `study_tasks.py`, `task_store.py` y `tests/`. Si faltan, pide resolver el bloqueo: ejecutar comandos no crea esos archivos.

En PowerShell 7:

```powershell
.venv\Scripts\python.exe study_tasks.py --help
.venv\Scripts\python.exe study_tasks.py list
.venv\Scripts\python.exe study_tasks.py add "Repasar agentes"
.venv\Scripts\python.exe study_tasks.py list
.venv\Scripts\python.exe study_tasks.py complete 1
.venv\Scripts\python.exe study_tasks.py list
.venv\Scripts\python.exe -m unittest discover -s tests -v
```

En Bash:

```bash
.venv/bin/python study_tasks.py --help
.venv/bin/python study_tasks.py list
.venv/bin/python study_tasks.py add "Repasar agentes"
.venv/bin/python study_tasks.py list
.venv/bin/python study_tasks.py complete 1
.venv/bin/python study_tasks.py list
.venv/bin/python -m unittest discover -s tests -v
```

#### C# con .NET: ejecutar y probar

Comprueba que Squad ha sustituido el saludo de la consola y la prueba vacía por la implementación acordada. Si solo quedan las plantillas, pide resolver el bloqueo: un proyecto que compila no demuestra que el gestor exista.

En PowerShell 7 o Bash:

```text
dotnet run --project src/StudyTasks -- --help
dotnet run --project src/StudyTasks -- list
dotnet run --project src/StudyTasks -- add "Repasar agentes"
dotnet run --project src/StudyTasks -- list
dotnet run --project src/StudyTasks -- complete 1
dotnet run --project src/StudyTasks -- list
dotnet test tests/StudyTasks.Tests/StudyTasks.Tests.csproj --verbosity normal
```

El separador `--` envía los argumentos a la aplicación. No ejecutes desde la carpeta del proyecto C#: el contrato define la ruta de datos relativa al directorio de trabajo de la raíz.

### Paso 3: comprobar el resultado antes de continuar

La ayuda debe estar en español, la tarea debe conservar su ID y aparecer completada en la última consulta. La suite debe informar de pruebas reales ejecutadas: cero casos o solo la prueba vacía no cuentan como éxito. Si un comando falla, conserva su salida y pide una corrección acotada; no añadas funciones para justificar el fallo.

## Ejercicio 4: revisar, fallar y corregir

Tiempo: minutos 60-72, 12 minutos. Objetivo: contrastar el contrato con pruebas y revisión humana.

### Paso 1: pedir una revisión de solo lectura

Pide una revisión de solo lectura antes de reparar.

Versión en español:

```text
Solo revisa; no edites código de la aplicación.

- Inspecciona el manejo de JSON mal formado, las entradas inválidas, los accesos a archivos no previstos, los secretos y los cambios fuera del alcance acordado según los *charters* y el *routing*.
- Compara las pruebas reales con cada caso de aceptación de `docs/spec.md`.
- Resume los hallazgos, sus evidencias y un plan mínimo de reparación.

Selecciona los revisores según sus charters y el routing, buscando una revisión
independiente del trabajo implementado cuando el equipo lo permita. Justifica
las elecciones e informa de las revisiones realmente ejecutadas.
Usa como máximo dos ejecuciones independientes. No afirmes que una prueba
se ejecutó si no lo hizo.

Espera la aprobación humana antes de corregir; no hagas commit ni push.
```

Versión en inglés:

```text
Review only; do not edit application code.

- Inspect malformed JSON handling, invalid input, unintended file access, secrets and changes outside the agreed scope according to the *charters* and *routing*.
- Compare real tests with every acceptance case in `docs/spec.md`.
- Summarize findings, their evidence and a minimal repair plan.

Select reviewers based on their charters and routing, seeking an independent
review of the implementation when the team permits it. Justify the choices
and report the reviews actually executed.
Use at most two independent executions. Do not claim a test ran unless it did.

Wait for human approval before fixes; do not commit or push.
```

### Paso 2: comprobar un error desde la terminal

La tabla siguiente describe argumentos de la aplicación, no comandos independientes del *shell*. Conserva el mismo ejecutable utilizado en el ejercicio 3. Por ejemplo, comprueba el título vacío con solo el bloque de tu lenguaje y sistema.

#### Python: comprobar el título vacío

En PowerShell 7:

```powershell
.venv\Scripts\python.exe study_tasks.py add "   "
$LASTEXITCODE
```

En Bash:

```bash
.venv/bin/python study_tasks.py add "   "
echo $?
```

#### C# con .NET: comprobar el título vacío

En PowerShell 7 o Bash:

```text
dotnet run --project src/StudyTasks -- add "   "
```

Para consultar el código de salida de este último comando, usa `$LASTEXITCODE` en PowerShell o `echo $?` en Bash inmediatamente después de ejecutarlo. Debe aparecer un mensaje de error en español y un código distinto de `0`. Vuelve a ejecutar `list` con el mismo prefijo y comprueba que no se añadió una tarea. Para el caso de ID inexistente, elige uno que no aparezca en esa lista y úsalo como argumento de `complete`.

### Paso 3: contrastar los casos de aceptación

| Caso | Resultado esperado |
| :--- | :--- |
| Listar sin archivo | Mensaje de lista vacía, salida 0, sin crear el archivo |
| Añadir y volver a abrir | Misma tarea, mismo ID y estado pendiente |
| Añadir un segundo título | Otro ID; ambas tareas siguen presentes |
| Completar y volver a listar | La tarea aparece completada tras otra ejecución |
| Completar dos veces | Éxito y mismo estado, sin duplicados |
| `add "   "` | Error y archivo sin cambios |
| Títulos de 120 y 121 puntos de código | Se acepta el primero y se rechaza el segundo |
| Título con acentos y un emoji | Se conserva al escribir y leer JSON |
| `complete 0`, `complete -1`, `complete abc` | Error sin cambiar datos |
| Completar un ID inexistente | Error sin cambiar datos |
| JSON mal formado, objeto en vez de lista o ID duplicado | Error y bytes originales intactos |
| ID booleano o `completed` como cadena | Error de esquema sin sobrescritura |

Cada fila debe tener al menos una prueba automatizada; agrupar varias entradas en una prueba parametrizada es válido. En directo prioriza el flujo feliz, título vacío y completar un ID inexistente. Los demás deben estar en la suite y revisarse mediante sus resultados.

También puedes pedir a Squad que compruebe la tabla anterior sobre la aplicación creada. Mantén seleccionado el agente *custom* de Squad, proporciona la tabla y solicita solo ejecución y un informe con comandos, resultados y casos pendientes, sin cambios de código. Deja que el coordinador seleccione los especialistas según los *charters* y el *routing*; concede únicamente los permisos que entiendas. Si faltan pruebas o aparece un fallo, no autorices su reparación hasta el siguiente paso.

### Paso 4: autorizar una reparación y repetir las pruebas

El tropiezo del taller es deliberado: no des por hecho que la generación habrá cubierto todo. Si aparece un fallo, aprueba una reparación pequeña y repite el caso y la suite con el comando de pruebas de tu lenguaje en el [ejercicio 3](#ejercicio-3-delegar-la-implementación). Si todos pasan, no introduzcas un bug artificial: explica qué error habría detectado una de las pruebas.

  Si tienes que realizar una reparación, encárgala al agente *custom* de Squad indicando el hallazgo, la evidencia y el alcance autorizado, sin nombrar un miembro. El coordinador debe elegir a quién delegarla según los charters y el routing. Durante esta práctica no la hagas tú directamente, aunque en la vida real podrías realizar pequeñas correcciones por productividad.

## Ejercicio 5: recuperar memoria en otra interfaz

Tiempo: minutos 72-82, 10 minutos. Objetivo: separar la memoria del equipo de una conversación larga.

### Paso 1: cambiar de interfaz sin escrituras simultáneas

Termina las operaciones de escritura de VS Code y cierra su conversación activa. Abre otra sesión desde la misma raíz con Copilot CLI.

```text
copilot --agent squad --additional-mcp-config "@.mcp.json"
```

Este comando carga explícitamente el servidor `squad_state` configurado durante la preparación. Revisa los avisos de confianza y comprueba su disponibilidad en esta sesión; no presupongas que hereda la conexión MCP del editor.

### Paso 2: recuperar y comprobar las decisiones

Mantén la aprobación manual. Pide recuperar contexto sin copiar de nuevo la especificación.

Versión en español:

```text
Lee el estado persistido del equipo y la especificación del proyecto.

Usa las herramientas disponibles para leer las decisiones
y los historiales. Puedes leer directamente la especificación y los charters.
Si no cuentas con herramientas disponibles o falla, informa del impedimento; no sustituyas
silenciosamente la comprobación por una lectura directa del estado.

No cambies archivos ni implementes funcionalidades.

Explica el almacenamiento de tareas que acordamos, el comportamiento ante

JSON mal formado y los roles de los cinco especialistas adicionales.

Cita los archivos locales reales.

Distingue una decisión compartida de una entrada en el historial individual de un agente.

Explica una delegación registrada, las responsabilidades del charter que motivaron la elección del miembro y la evidencia de su ejecución real.

Si algo no se guardó, indícalo en lugar de reconstruirlo como un hecho.
```

Versión en inglés:

```text
Read the persisted team state and the project specification.

Use MCP tools from the squad_state server to read decisions and histories.
You may read the specification and charters directly.
If MCP is unavailable or fails, report the blocker; do not silently
substitute direct state reads for the MCP check.

Do not change files or implement features.

Explain our agreed task storage, the behavior for malformed JSON and the roles of the five additional specialists. Cite the actual local files.

Distinguish a shared decision from an individual agent history entry.

Explain one recorded delegation, the charter responsibilities that motivated the member selection and the evidence of its actual execution.

If something was not saved, say so instead of reconstructing it as a fact.
```

Comprueba tú los archivos citados. En la configuración Markdown habitual encontrarás decisiones globales compartidas por todos los miembros (arquetipos) del Squad en `.squad/decisions.md`, aportaciones pendientes en `.squad/decisions/inbox/` e historiales o memoria propia de cada miembro bajo `.squad/agents/`. Puede haber decisiones aún pendientes de consolidar: no afirmes que desaparecieron sin revisar el inbox.

## Ejercicio 6: agentes con distintos modelos en Copilot CLI

Tiempo: minutos 82-97, 15 minutos. Objetivo: configurar dos modelos distintos para dos especialistas y contrastar lo configurado con sus lanzamientos y ejecuciones reales.

Punto de partida: el ejercicio 5 está completado y trabajas en la misma raíz de práctica, con GitHub Copilot CLI y Squad 1.1.0. No cambies al shell interactivo `squad` ni incorpores el SDK a la aplicación: son rutas de ejecución distintas. Si tu cuenta no permite utilizar dos modelos o no expone selección por lanzamiento, trabaja en pareja o revisa la demostración del instructor, registrando esa limitación.

### Paso 1: elegir especialistas y modelos disponibles

En la sesión CLI del ejercicio 5, consulta `/model`. El catálogo de tu cuenta y cliente es la referencia para elegir dos IDs distintos; no asumas que los modelos de una guía están disponibles ni habilites cargos adicionales. Elegir un modelo de sesión no asigna por sí mismo modelos diferentes a los especialistas.

Envía una versión de este encargo. Squad elige los miembros según sus charters y el routing, no por nombres preestablecidos.

Versión en español:

```text
Propón dos revisiones pequeñas y de solo lectura sobre esta aplicación:
una de ayuda y mensajes de consola y otra de los casos de prueba para JSON
corrupto. No ejecutes las revisiones todavía.

Selecciona dos especialistas distintos según sus charters y el routing.
Indica el rol, el identificador real de su directorio bajo .squad/agents/
y qué responsabilidad justifica cada elección. No crees nuevos miembros.

Usaremos un modelo distinto para cada especialista en Copilot CLI.
Muestra el plan y espera mi aprobación y la configuración de los modelos.
No modifiques archivos, instales paquetes, hagas commit ni push.
```

Versión en inglés:

```text
Propose two small read-only reviews of this application:
one of console help and messages and one of test cases for corrupt JSON.
Do not run the reviews yet.

Select two distinct specialists according to their charters and routing.
Report each role, the actual directory ID under .squad/agents/, and the
responsibility that justifies the selection. Do not create new members.

We will use a different model for each specialist in Copilot CLI.
Show the plan and wait for my approval and model configuration.
Do not modify files, install packages, commit or push.
```

Comprueba los dos IDs en `.squad/agents/` y sus charters. Aprueba el reparto cuando encaje con las responsabilidades y conserva el texto de esa propuesta: lo adjuntarás a la nueva sesión del paso 3. Sal de la conversación CLI para configurar desde la terminal de la práctica. Ejecuta `squad config model` y anota las asignaciones anteriores de esos dos miembros; las necesitarás al terminar.

### Paso 2: guardar una asignación por agente

Las claves de `agentModelOverrides`, dentro de `.squad/config.json`, son los IDs de directorio, no necesariamente los nombres mostrados en el chat. `defaultModel` es la preferencia global para quienes no tengan una asignación individual; no la cambies para esta demostración. Conserva `stateBackend: "local"` y los demás ajustes del proyecto.

En PowerShell 7, introduce los dos IDs reales aprobados y los dos modelos elegidos del catálogo:

```powershell
$firstAgent = Read-Host 'First agent directory ID'
$secondAgent = Read-Host 'Second agent directory ID'
$firstModel = Read-Host 'First available model ID'
$secondModel = Read-Host 'Second available model ID'
foreach ($selection in @($firstAgent, $secondAgent, $firstModel, $secondModel)) {
  if ([string]::IsNullOrWhiteSpace($selection)) { throw 'Agent and model IDs must not be empty.' }
}
if ($firstAgent -eq $secondAgent -or $firstModel -eq $secondModel) {
    throw 'Choose two distinct agents and two distinct models.'
}
squad config model "$firstModel" --agent "$firstAgent"
if ($LASTEXITCODE -ne 0) { throw 'First model assignment failed; inspect configuration before continuing.' }
squad config model "$secondModel" --agent "$secondAgent"
if ($LASTEXITCODE -ne 0) { throw 'Second model assignment failed; inspect configuration before continuing.' }
squad config model
```

En Bash, utiliza esta alternativa dentro del mismo proyecto:

```bash
read -r -p 'First agent directory ID: ' first_agent
read -r -p 'Second agent directory ID: ' second_agent
read -r -p 'First available model ID: ' first_model
read -r -p 'Second available model ID: ' second_model
if [ -z "$first_agent" ] || [ -z "$second_agent" ] || [ -z "$first_model" ] || [ -z "$second_model" ]; then
  printf '%s\n' 'Agent and model IDs must not be empty.'
elif [ "$first_agent" = "$second_agent" ] || [ "$first_model" = "$second_model" ]; then
  printf '%s\n' 'Choose two distinct agents and two distinct models.'
else
  squad config model "$first_model" --agent "$first_agent" &&
    squad config model "$second_model" --agent "$second_agent" &&
    squad config model
fi
```

No avances si algún comando falla. La CLI valida IDs de agentes y su propio catálogo de modelos, pero eso no demuestra que tu cuenta tenga acceso al modelo. Comprueba en `.squad/config.json` que aparecen ambos IDs con valores distintos. Los comandos modifican preferencias persistentes; no ejecutan modelos.

La resolución documentada da prioridad a estas capas, en este orden:

```text
Override explícito de la tarea
  > agentModelOverrides[agente] o defaultModel
  > modelo de sesión
  > Preferred del charter
  > selección automática según tarea
  > modelo predeterminado
```

Una asignación individual gana frente a `defaultModel`, al modelo de sesión y al charter. `auto` expresa ausencia de preferencia en una capa, no un modelo concreto; no lo uses como uno de los dos modelos de la demostración. El resolver puede recurrir a un fallback si conoce que el modelo no está disponible. Guardar una preferencia no garantiza que la interfaz ni el runtime la apliquen.

### Paso 3: ejecutar las revisiones y observar los lanzamientos

Abre una sesión nueva para que el coordinador vuelva a leer la configuración:

```text
copilot --agent squad --additional-mcp-config "@.mcp.json"
```

Adjunta o pega la propuesta aprobada en el paso 1, con los dos IDs reales y las revisiones acordadas, y después usa una de estas versiones. La configuración persiste los modelos, no esa propuesta conversacional. No añadas un override de modelo para la tarea, porque ocultaría las asignaciones que quieres comprobar.

Versión en español:

```text
Ejecuta las dos revisiones de solo lectura cuyo reparto acabamos de aprobar.
Recupera los especialistas del plan y sus preferencias agentModelOverrides
de .squad/config.json. Respeta sus charters y el routing.

En cada lanzamiento solicita el modelo resuelto para ese miembro mediante
la capacidad real de selección de modelo de la herramienta de lanzamiento.
No basta escribir el nombre del modelo en el texto del encargo.

Muestra por separado el ID y rol del miembro, el modelo configurado,
el modelo solicitado en la llamada, el modelo reportado por el runtime
si está disponible y la referencia de cada evidencia real.
Si hay un fallback, una restricción o falta información del runtime,
decláralo: no infieras el modelo usado de la configuración ni del resultado.

No modifiques código, pruebas, datos ni configuración. No instales paquetes,
hagas commit ni push. Como máximo, dos trabajos independientes a la vez.
Si no puedes lanzar especialistas con modelos diferentes, informa del
impedimento y espera; no simules dos agentes en una sola respuesta.
```

Versión en inglés:

```text
Run the two read-only reviews whose ownership plan we just approved.
Recover the specialists from the plan and their agentModelOverrides
preferences from .squad/config.json. Respect their charters and routing.

For each launch, request the resolved model for that member using the
launch tool's actual model-selection capability. Writing the model name
inside the task prompt is not sufficient.

Report separately the member ID and role, configured model, model requested
in the tool call, runtime-reported model if available, and references to
each real piece of evidence. Declare fallbacks, restrictions or missing
runtime information; do not infer the used model from config or output.

Do not modify code, tests, data or configuration. Do not install packages,
commit or push. Run at most two independent jobs at a time.
If you cannot launch specialists with different models, report the blocker
and wait; do not simulate two agents in a single response.
```

Inspecciona las llamadas de lanzamiento y sus resultados en CLI. Registra el modelo solicitado mediante el argumento real de la herramienta, no mediante la explicación del coordinador. Busca el modelo reportado en los metadatos de ejecución o los registros locales que tu cliente exponga; si no aparece, registra «no expuesto». No publiques registros ni proyectes tokens o contenido privado.

### Paso 4: contrastar las evidencias y restaurar preferencias

Distingue estas tres evidencias para cada uno de los dos especialistas:

| Evidencia | Qué compruebas | Qué no demuestra por sí sola |
| :--- | :--- | :--- |
| Configuración guardada | ID y valor en `agentModelOverrides` | Que el agente se lanzó o utilizó ese modelo |
| Modelo solicitado | Parámetro real de la llamada de lanzamiento | Que el runtime lo aceptó sin fallback |
| Modelo reportado | Metadatos o registros de la ejecución concreta | Que la revisión sea correcta |

Da por demostrada la ejecución con modelos distintos solo si puedes relacionar las dos ejecuciones reales con dos modelos reportados distintos. Si solo hay modelos solicitados distintos, concluye «configuración y solicitud verificadas; modelos efectivos no confirmados». Si ambos acaban en el mismo fallback, no afirmes que se ejecutaron con modelos diferentes. Tampoco infieras el modelo por el estilo de la respuesta.

Contrasta con VS Code: según la documentación de Squad 1.1.0, allí los agentes usan el modelo de sesión del selector, no una selección diferente por lanzamiento. No presentes guardar este JSON como prueba de ejecución multimodelo en el editor. En cualquier cliente, comprueba las capacidades reales de la versión que estás utilizando.

Para terminar, restaura las preferencias anteriores de los dos miembros. Introduce para cada uno el modelo previo que anotaste en el paso 1; deja la entrada vacía únicamente si no tenía una asignación individual. Ejecuta la alternativa de tu shell:

```powershell
foreach ($agent in @($firstAgent, $secondAgent)) {
    $previousModel = Read-Host "Previous model ID for $agent (empty only if none)"
    if ([string]::IsNullOrWhiteSpace($previousModel)) {
        squad config model --clear --agent "$agent"
    } else {
        squad config model "$previousModel" --agent "$agent"
    }
    if ($LASTEXITCODE -ne 0) { throw 'Model preference restoration failed; inspect configuration.' }
}
squad config model
```

```bash
for agent in "$first_agent" "$second_agent"; do
  read -r -p "Previous model ID for $agent (empty only if none): " previous_model
  if [ -z "$previous_model" ]; then
    squad config model --clear --agent "$agent" || break
  else
    squad config model "$previous_model" --agent "$agent" || break
  fi
done
squad config model
```

No avances si la restauración falla. Comprueba que los dos miembros recuperaron sus valores anteriores y que `defaultModel` y los otros ajustes no cambiaron. No reemplaces todo `.squad/config.json` ni elimines preferencias ajenas. Verifica las revisiones contra los archivos citados: usar dos modelos no demuestra calidad, consenso ni independencia de sus errores.

Referencias: [selección por agente y limitación de VS Code en Squad 1.1.0](https://github.com/bradygaster/squad/blob/v1.1.0/docs/src/content/docs/features/model-selection.md) y [comandos de configuración de modelos](https://github.com/bradygaster/squad/blob/v1.1.0/packages/squad-cli/src/cli/commands/config.ts).

## Cierre y evidencias

Tiempo: minutos 97-105, 8 minutos.

Revisa los cambios locales antes de decidir qué conservar.

```text
git status --short
git diff
```

`git diff` no muestra el contenido de archivos nuevos sin seguimiento: ábrelos también en VS Code, especialmente los charters, decisiones y pruebas. No se pide hacer commit ni publicar el proyecto durante el taller.

Usa esta lista para ambos lenguajes; registra la versión de Python o del SDK .NET según el proyecto revisado:

- [ ] La aplicación cumple el contrato del ejercicio 2
- [ ] Las tareas sobreviven al cierre y reapertura del proceso
- [ ] Las pruebas usan directorios temporales y no modifican mis datos de práctica
- [ ] Hay pruebas reales, no cero casos ni solo la prueba vacía de xUnit
- [ ] Registro la versión del lenguaje o SDK, el número de pruebas y el resultado real
- [ ] Puedo localizar a quién delegó Squad, qué aportó cada especialista y cómo su charter justificó la elección
- [ ] Distingo modelo configurado, solicitado y reportado; registro lo comprobado en el ejercicio 6 y restauro las preferencias anteriores

Responde: ¿qué tarea pequeña resolverías con un único asistente?, ¿qué trabajo separarías entre especialistas?, ¿qué permiso no concederías automáticamente? Contrasta tu salida con la [lista del temario](00%20-%20temario.md).
