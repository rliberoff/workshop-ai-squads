# 👷🏻 Squad: Equipos de Agentes IA para Cualquier Proyecto con GitHub Copilot 🏗️

Workshop práctico sobre cómo configurar y coordinar equipos de agentes de IA con Squad y GitHub Copilot dentro de repositorios de proyectos.

## De qué va

Un solo Copilot te ayuda. Un equipo entero de agentes... te da reuniones de seguimiento con quien no cobra horas extra.

Hasta ahora le pedías cosas a GitHub Copilot una a una. En este taller de *Context Engineering* damos un paso más: montamos una cuadrilla de agentes que vive dentro de tu repositorio, con su líder, sus especialistas y su propia memoria del proyecto.

Usaremos [Squad](https://github.com/bradygaster/squad), el proyecto open source de Brady Gaster, para que el coordinador seleccione especialistas y reparta trabajo según sus charters y el routing. Le pediremos objetivos y entregables, no encargos dirigidos a miembros concretos. Las decisiones y el historial quedan en archivos revisables. Delegar no significa desentenderse: el humano define los límites, comprueba las asignaciones y los resultados y decide qué acepta.

## El taller en un vistazo

| Aspecto | Alcance |
| :--- | :--- |
| Duración | 105 minutos presenciales |
| Material | Markdown autoguiado en español |
| Audiencia | Estudiantes y profesionales principiantes en desarrollo agéntico |
| Conocimientos | No se imparten programación, terminal ni Git |
| Proyecto | Gestor de tareas de estudio por consola, con persistencia JSON |
| Tecnologías | Python o .NET 10 con C#, con alternativas integradas en cada paso |
| Interfaces | GitHub Copilot en VS Code y Copilot CLI |
| Equipo | Cuatro roles base y cinco especialistas adicionales |
| Ejecución | Aplicación local; Copilot necesita conexión a Internet |
| Fuera de alcance | Nube, Terraform, servidores web y automatización desatendida |

## Qué aprenderás

- Distinguir cuándo basta un asistente y cuándo compensa coordinar un equipo
- Inicializar Squad y ampliar su equipo con responsabilidades verificables
- Formular objetivos generales y observar cómo Squad reparte trabajo según los charters, sin ediciones simultáneas sobre los mismos archivos
- Inspeccionar roles, decisiones e historiales y recuperar contexto en otra sesión
- Configurar modelos distintos por agente en Copilot CLI y contrastar configuración, lanzamiento y reporte del runtime
- Revisar código, pruebas y límites antes de aceptar cambios
- Reconocer errores habituales: requisitos ambiguos, alcance excesivo y memoria incorrecta

## Por dónde empezar

1. Lee el [temario](docs/00%20-%20temario.md).
2. Antes de asistir, sigue la [preparación común](docs/01%20-%20preparacion.md): instala herramientas, autentícate y completa la sección [Antes de la sesión: preparar el proyecto](docs/04%20-%20ejercicios.md#antes-de-la-sesión-preparar-el-proyecto) de la guía integrada.
3. Revisa la [lista de preparación](docs/01%20-%20preparacion.md#lista-de-preparación) y detente: todavía no encargues trabajo a Squad ni implementes la aplicación.
4. Durante la sesión, sigue los [seis ejercicios](docs/04%20-%20ejercicios.md) en orden y termina con el cierre. Ahí tendrás tu primera conversación con Squad para formar el equipo. En cada paso técnico elige la alternativa de Python o .NET correspondiente a tu proyecto y tu shell.

Una sola guía reúne las acciones, los comandos y los mensajes de ambos lenguajes en el orden de ejecución. Las acciones comunes de Squad aparecen una sola vez; no necesitas documentos de itinerarios independientes. Cada paso indica qué hacer, qué comprobar y cómo continuar.

Para impartirlo, consulta la [guía del instructor](docs/05%20-%20instructor.md). Consulta también las [referencias oficiales](#referencias).

## Acceso y participación

Necesitas portátil, conexión a Internet, cuenta de GitHub y acceso activo a GitHub Copilot. Copilot Free permite participar, pero no garantizamos que su cuota o sus funciones disponibles basten para todas las prácticas de Squad. Antes de venir, comprueba tu inicio de sesión y revisa el plan y el consumo disponible. La ejecución de Squad se comprueba durante los ejercicios, no en una práctica previa.

Si una función no está disponible o se agota la cuota, trabaja por parejas con una cuenta habilitada o sigue la demostración del instructor y realiza la revisión de evidencias. No compartas contraseñas ni tokens y no es necesario comprar una licencia para asistir.

Qué te llevas: un equipo configurado en tu proyecto si tu acceso lo permite, una aplicación local revisada y criterios para decidir qué delegar y qué no. En la modalidad de observación practicarás la configuración y revisión sobre las evidencias del instructor, sin simular una ejecución propia.

Casco y chaleco: opcionales, pero el emoji obliga.

## Referencias

- [Squads Documentation](https://bradygaster.github.io/squad/)
- [Squads GitHub Repository](https://github.com/bradygaster/squad)

## Licencia

Este proyecto se distribuye bajo la licencia MIT. Consulta [LICENSE](LICENSE).
