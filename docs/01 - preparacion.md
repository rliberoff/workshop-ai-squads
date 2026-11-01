# Preparación del entorno

## Antes de venir

Reserva entre 30 y 45 minutos fuera de los 105 minutos del taller; las instalaciones o la activación de tu cuenta pueden requerir más tiempo. Necesitas conexión a Internet para instalar herramientas y usar Copilot, aunque la aplicación y sus datos funcionen localmente.

Sigue este orden. Todo lo que aparece en esta página se hace antes de la sesión:

1. Comprueba tu cuenta y el acceso disponible.
2. Instala las herramientas comunes usando solo la sección de tu sistema.
3. Autentícate en Copilot CLI y en VS Code.
4. Abre los [ejercicios](04%20-%20ejercicios.md#antes-de-la-sesión-preparar-el-proyecto) y completa solo su sección «Antes de la sesión»: runtime, repositorio de práctica e inicialización de Squad. Elige Python o .NET en cada paso técnico según el proyecto que vas a preparar.
5. Revisa la lista de preparación. Cuando empiece el taller, abre los ejercicios desde el ejercicio 1.

El clon de este material sirve para leer, no para construir la aplicación. La carpeta nueva de práctica será el lugar de trabajo de toda la sesión. No implementes todavía el gestor de tareas.

## Cuenta y licencia

1. Accede a tu cuenta de GitHub y comprueba que tienes Copilot activado en sus ajustes.
2. Consulta tu plan y el consumo disponible antes de la sesión.
3. Si eres estudiante, solicita y activa el beneficio de GitHub Education con antelación: verificar la condición de estudiante y activar Copilot son pasos diferentes y pueden tardar días.

Consulta los [planes vigentes](https://docs.github.com/en/copilot/get-started/plans) y el [acceso para estudiantes](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students).

El inicio de sesión no garantiza que tu plan permita todas las funciones de Squad ni que la cuota alcance para toda la práctica. Lo comprobarás durante los ejercicios con el instructor; si hay un bloqueo, trabajarás por parejas u observarás la demostración. No necesitas configurar ni probar un equipo por adelantado.

## Herramientas comunes

| Herramienta | Referencia del taller | Comprobación |
| :--- | :--- | :--- |
| Git | Versión estable instalada | `git --version` |
| VS Code | Versión estable actual con GitHub Copilot habilitado | Abrir Copilot Chat |
| Shell de Windows | PowerShell 7, no Windows PowerShell 5.1 | `$PSVersionTable.PSVersion` |
| Shell de Linux, macOS o WSL | Bash | `bash --version` |
| Node.js | LTS compatible, como 24; mínimo 22.5 para Squad | `node --version` |
| npm | 10 o superior | `npm --version` |
| Squad CLI | 1.1.0 estable | `squad --version` |
| GitHub Copilot CLI | 1.0.105 como referencia del repositorio | `copilot --version` |

Instala [Git](https://git-scm.com/downloads), [VS Code](https://code.visualstudio.com/download), [PowerShell](https://learn.microsoft.com/powershell/scripting/install/installing-powershell) y [Node.js](https://nodejs.org/en/download) desde sus distribuidores oficiales. Si necesitas permisos de administración, realiza la instalación tú mismo siguiendo su procedimiento; no apruebes scripts desconocidos.

## Windows con PowerShell 7

Abre PowerShell 7 y comprueba los prerrequisitos instalados.

```powershell
$PSVersionTable.PSVersion
git --version
node --version
npm --version
```

Necesitas PowerShell 7 y Node 22.5 o superior; utiliza una versión LTS compatible. Si falta un comando, instala esa herramienta y abre una terminal nueva.

Instala las versiones de referencia de las dos herramientas del taller.

```powershell
npm install -g @bradygaster/squad-cli@1.1.0
npm install -g @github/copilot@1.0.105
squad --version
copilot --version
```

Si ya las tienes mediante `npm`, `winget` u otro canal, no superpongas instalaciones globales: comprueba con el instructor la versión y conserva un solo canal. Las versiones fijadas son una referencia reproducible, no una invitación a degradar una instalación de uso diario sin revisarlo.

## Linux, macOS y WSL

Comprueba los prerrequisitos desde la terminal donde realizarás el taller.

```bash
bash --version
git --version
node --version
npm --version
```

Instala las versiones de referencia si todavía no tienes estas herramientas mediante otro canal.

```bash
npm install -g @bradygaster/squad-cli@1.1.0
npm install -g @github/copilot@1.0.105
squad --version
copilot --version
```

No uses `sudo npm install` como solución automática a permisos: utiliza una instalación de Node para tu usuario. En macOS abre Bash para estos ejemplos, aunque tu shell habitual sea `zsh`.

En WSL instala Git, Node, Squad, Copilot y el runtime elegido dentro de Linux. Abre esa carpeta en VS Code mediante WSL y mantén el proyecto en el sistema de archivos de Linux. No mezcles un entorno virtual Python de Windows con WSL ni ejecutes `dotnet.exe` de Windows sobre el proyecto Linux.

## Autenticación

Antes de crear el proyecto, abre Copilot CLI desde una carpeta sin datos sensibles. Esto solo comprueba tu inicio de sesión, no el funcionamiento de Squad.

```text
copilot
```

Sigue la autenticación del navegador o usa `/login` dentro de la sesión si se solicita. Sal con Ctrl+C al terminar. Inicia también sesión en GitHub desde VS Code y confirma que Copilot Chat responde.

Antes de avanzar: ambas interfaces reconocen tu cuenta. No mantengas esta sesión de CLI abierta para escribir mientras uses VS Code.

## Preparar el repositorio de práctica

Completa únicamente los tres pasos de la sección [Antes de la sesión: preparar el proyecto](04%20-%20ejercicios.md#antes-de-la-sesión-preparar-el-proyecto). Allí comprobarás Python o el SDK .NET, crearás el repositorio con la alternativa de tu lenguaje y prepararás el coordinador con `squad init` en un paso común.

El paso 3 incluye [configurar las herramientas MCP](04%20-%20ejercicios.md#configurar-las-herramientas-mcp), entre ellas el servidor `squad_state`, que da acceso al estado persistente del equipo. Revisa la configuración generada, conecta el servidor en VS Code y comprueba que ofrece herramientas. No envíes una tarea previa a los agentes: la primera lectura real mediante MCP se realizará en el ejercicio 1, después de formar el equipo.

Al terminar el paso 3 de esa sección, revisa la [lista de preparación](#lista-de-preparación) y detente. El coordinador está preparado, pero todavía no has configurado el equipo ni encargado trabajo a los agentes. Durante el taller, continúa en el ejercicio 1 del mismo documento; el contexto técnico se entrega en el ejercicio 2, cuando el equipo ya está configurado.

## Límites de seguridad

- Trabaja únicamente en el repositorio de práctica, nunca desde tu carpeta personal completa
- Lee cada solicitud de permisos y concede solo lo necesario
- No uses `--yolo`, aprobación global de herramientas, ejecución desatendida ni auto-merge
- No añadas tokens, contraseñas, documentos privados ni datos personales de estudiantes
- Revisa los cambios también en los archivos de memoria del equipo
- No ejecutes simultáneamente sesiones de escritura en VS Code y CLI

Las instrucciones y los charters expresan intención; no son un sandbox. Tampoco una carpeta marcada como confiable garantiza aislamiento completo. Las pruebas y la revisión humana siguen siendo necesarias.

## Lista de preparación

- [ ] Tengo cuenta de GitHub y sé qué plan de Copilot está activo
- [ ] He revisado mi plan y el consumo disponible sin habilitar cargos adicionales
- [ ] VS Code y Copilot CLI funcionan en el mismo entorno
- [ ] Squad está instalado, he revisado `squad doctor` y el archivo del coordinador existe
- [ ] He revisado `.mcp.json` y el servidor `squad_state` ofrece herramientas en VS Code, sin permisos globales
- [ ] He instalado el runtime o SDK del proyecto que voy a utilizar
- [ ] He completado la preparación del proyecto en los ejercicios y sé cuál es su carpeta raíz
- [ ] Tengo una carpeta de práctica sin secretos y distinta del repositorio del taller
- [ ] He descargado dependencias y runtimes antes de asistir

Con esta lista completada, tu siguiente acción durante el taller es el [ejercicio 1: formar y ampliar el equipo](04%20-%20ejercicios.md#ejercicio-1-formar-y-ampliar-el-equipo). No repitas instalaciones ni `squad init`.

## Problemas frecuentes

| Síntoma | Acción |
| :--- | :--- |
| No aparece un comando | Abre otra terminal y comprueba su instalación y PATH |
| PowerShell bloquea un script npm | Prueba `npm.cmd`; no desactives globalmente las políticas |
| Squad no aparece en VS Code | Comprueba `.github/agents/squad.agent.md` y vuelve a abrir la sesión |
| Fallan funciones o se agota el acceso | Pasa a pareja u observación; no compres para desbloquear la clase |
| Squad no encuentra su equipo | Sitúate en la raíz del proyecto y ejecuta `squad doctor` |
| `squad_state` no arranca o sus herramientas no aparecen | Revisa la conexión MCP, la salida del servidor y las herramientas disponibles para Squad según el paso 3 de los ejercicios; no reinicialices el equipo |
| Error de SDK .NET | Sigue el paso de verificación del lenguaje en los ejercicios, no basta el runtime |
| Windows y WSL muestran resultados distintos | Elige un entorno completo y vuelve a abrir allí el proyecto |
