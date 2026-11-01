# Guía del instructor

## Intención didáctica

El resultado no es «generar más código»: es observar delegación real, contexto persistente y responsabilidad humana. El gestor de tareas mantiene el dominio sencillo para que la atención se centre en Squad.

El participante formula objetivos y límites; Squad selecciona especialistas y reparte trabajo según los charters y el routing. No proyectes mensajes que asignen acciones a nombres concretos ni reemplaces las decisiones del coordinador por un reparto manual. Pide evidencias de la selección, las ejecuciones y los resultados; si el reparto no encaja con los charters, solicita que lo revise y justifique antes de continuar.

Conserva cuatro arquetipos base y añade los cinco extras del [temario](00%20-%20temario.md). Explica que esta composición es una decisión del taller; Squad adapta el equipo al proyecto y no siempre crea cuatro roles idénticos. No cuentes el coordinador, Scribe ni Ralph como extras.

La duración aproximada es de 105 minutos con instalaciones previas. Tener nueve especialistas no implica ejecutar nueve sesiones simultáneas. El límite de dos trabajos independientes reduce consumo y colisiones, y permite mostrar dependencias sin saturar.

Conduce la sesión desde los [ejercicios](04%20-%20ejercicios.md), que integran las alternativas de Python y .NET dentro de cada paso, permitiendo que cada asistente elija su lenguaje. El inicio de sesión y la sección «Antes de la sesión: preparar el proyecto» se completan antes de venir, sin encargos a los agentes. Durante la clase, cada mesa elige el bloque técnico de su proyecto en el mismo documento; las acciones comunes de Squad no se repiten por lenguaje.

Explica la diferencia entre tres acciones: inicializar Squad prepara el coordinador; configurar el equipo guarda roles y responsabilidades; aprobar la especificación permite comenzar el código de la aplicación. En Python el entorno previo no contiene aplicación; en .NET contiene plantillas, no la solución. La primera conversación con Squad ocurre en el ejercicio 1 para formar el equipo; no se pide una práctica de delegación previa a estudiantes.

## Preparación del instructor

Con cierta antelación:

- Envía la [preparación](01%20-%20preparacion.md) y la guía integrada de ejercicios; solicita que preparen el lenguaje con el que trabajarán
- Explica que quienes cuenten con licencias `Free` de GitHub Copilot son bienvenidos; pero prevé parejas si las primeras tareas de los ejercicios revelan límites de acceso o cuota
- Recomienda solicitar GitHub Education antes del evento, sin prometer aprobación inmediata
- Comprueba conexión, permisos de instalación y acceso a los servicios de GitHub en el lugar
- Prepara una cuenta propia con acceso suficiente, sin proyectar secretos ni datos de facturación privados
- Ensaya por separado las alternativas de Python y .NET de la guía integrada, nunca contra el repositorio de material
- Comprueba manualmente ambos entornos de shell si están disponibles; registra los que no hayas probado
- No actualices Squad, Copilot, SDK ni modelos justo antes de impartirlo sin repetir el ensayo

En el ensayo, completa los [seis ejercicios](04%20-%20ejercicios.md) y conserva repositorios de demostración locales con estas etapas reales:

| Etapa | Contenido que debe poder mostrarse |
| :--- | :--- |
| Entorno | Runtime y CLI comprobados, sin aplicación completa |
| Equipo | Nueve especialistas con charters y routing |
| Contrato | Especificación aprobada y decisión persistente |
| Implementación | Aplicación y pruebas ejecutadas con resultados guardados |
| Revisión | Hallazgos o revisión sin hallazgos, reparaciones y prueba repetida |
| Memoria | Nueva sesión que recupera una decisión desde archivos |
| Modelos | Dos especialistas en CLI, modelos configurados y solicitados, reporte del runtime si existe y preferencias restauradas |

Estos repositorios los produce el ensayo del instructor: el material no incluye una solución preconstruida ni resultados ficticios. Guarda copias separadas o commits locales de tus repositorios de ensayo para mostrar una etapa sin borrar trabajo durante la clase. No publiques historiales con datos privados.

Si el ensayo supera el tiempo, reduce explicaciones o usa una etapa ya preparada; no elimines especialistas ni casos del contrato para acelerar silenciosamente. Registra el alcance que quedó observado y el que se ejecutó en vivo.

## Revisión técnica antes de abrir la sala

En el ensayo, respeta el mismo orden del participante: preparación común, sección de preparación del proyecto en la guía integrada y ejercicios 1 a 6, sin añadir una tarea preliminar. Comprueba tú la delegación al ensayar los ejercicios; no conviertas esa verificación del instructor en un requisito previo para estudiantes. Ejecuta los comandos del ejercicio 3 solo en la etapa de implementación, no en un entorno vacío o de plantillas. Conserva las versiones observadas. Para la herramienta común, comprueba:

```text
squad --version
copilot --version
squad doctor
git status --short
```

Comprueba que Squad aparece en VS Code y que `copilot --agent squad --additional-mcp-config "@.mcp.json"` carga el mismo equipo. No invoques `squad watch --execute`, no actives auto-merge ni uses aprobación global. El SDK de Squad no forma parte del temario.

Ensaya la [conexión MCP de `squad_state`](04%20-%20ejercicios.md#configurar-las-herramientas-mcp) con la versión 1.1.0 y el backend local. Comprueba las herramientas disponibles para el agente Squad y conserva una lectura real `squad_state_read` en VS Code durante el ejercicio 1 y otra en CLI durante el ejercicio 5, con su entrada, resultado y archivo contrastado. `squad doctor` y la presencia de `.mcp.json` no sustituyen estas evidencias. Prepara las descargas del servidor antes de abrir la sala; no añadas una conversación preliminar al recorrido del participante.

Explica la diferencia entre servidor MCP, herramientas y backend de estado: `squad_state` expone herramientas, `local` determina dónde se conserva la memoria y `data/tasks.json` pertenece a la aplicación. No necesitas otros servidores externos ni tokens para esta práctica. Si una política bloquea MCP, registra la limitación y utiliza pareja o demostración autorizada; no la eludas ni anuncies una lectura directa como prueba de MCP.

Valida estas equivalencias entre lenguajes: comandos, códigos de salida, orden por ID, estados, esquema JSON, títulos Unicode, rechazo de datos corruptos y persistencia entre procesos. Los mensajes pueden variar, pero han de estar en español y transmitir la misma información.

No anuncies compatibilidad probada con macOS o WSL basándote únicamente en haber leído sintaxis Bash. Diferencia siempre documentación contrastada, revisión estática y ejecución real.

## Guion de los 105 minutos

### Minutos 00-08: poner el marco

Pregunta: «¿Cuándo usarías una sola persona para un encargo y cuándo coordinarías varias especialidades?». Conecta la respuesta con el coste de coordinación.

Explica agente, coordinador, contexto y herramientas sin atribuir personalidad humana real a los roles. Un nombre Marvel facilita recordar responsabilidades, pero no aporta competencia por sí mismo.

Muestra el objetivo final de la consola en tu repositorio de ensayo y aclara que no vamos a estudiar sintaxis de Python, C# o Git. Explica también que «local» se refiere a aplicación y datos, no a inferencia sin Internet.

### Minutos 08-15: acceso y dos interfaces

Haz una comprobación breve de acceso. Quien tenga bloqueo pasa a pareja u observación; no detengas la sala para instalar.

Pide que cada mesa muestre la raíz de su práctica y el coordinador generado. No deben estar trabajando en el clon del material ni repetir `squad init`. Proyecta el mapa de recorrido de los ejercicios y señala en qué paso está el grupo antes de enviar cada mensaje.

Muestra el selector Squad en VS Code y el arranque en CLI desde el mismo repositorio. No hagas dos sesiones de escritura simultáneas. Reserva el cambio completo de sesión para el ejercicio 5.

Explica que el catálogo de modelos y las capacidades varían por plan. En Free/Student no exijas selección manual de un modelo de pago. Si una limitación impide Squad, utiliza tu demostración: no conviertas la sesión en una venta de licencias.

### Minutos 15-30: equipo y responsabilidad

Guía el ejercicio 1. Si el roster inicial tiene menos miembros, pide añadir los que faltan. Nueve especialistas es el requisito de esta práctica, no un supuesto sobre el valor predeterminado del producto.

Cuenta los cinco extras en pantalla y abre uno de sus charters. Pregunta: «¿Qué peticiones encajan con estas responsabilidades y qué límites tiene este miembro?». Producto y documentación no son el mismo rol; seguridad tampoco reemplaza al tester. Esto define competencias, no una asignación de las próximas tareas.

El uso de nombres alternativos por la política de casting es aceptable si los roles existen y los participantes conocen la correspondencia. Los mensajes posteriores son genéricos: no requieren adaptar nombres ni elegir manualmente a los destinatarios.

### Minutos 30-40: contrato antes de código

Guía el ejercicio 2. En su paso 1, cada mesa envía el contexto técnico de Python o .NET. En los pasos 2 y 3, todos proporcionan el mismo contrato y acuerdan el reparto y la aprobación. Asegúrate de que entregan también la tabla de casos de aceptación, no solo el mensaje que hace referencia a ella. El coordinador no puede leer por arte de magia un archivo de otro repositorio.

Pide que observen qué especialistas selecciona Squad para el plan, qué charters justifican cada elección y cómo propone resolver las dependencias. La persona aprueba el contrato y los límites, sin asignar cada entregable a un arquetipo concreto.

Pide que identifiquen la exclusión de nube y la respuesta a JSON corrupto. Muestra una decisión en disco y la diferencia entre una propuesta y un contrato aprobado.

Si el agente propone borrar datos corruptos, señala la desviación y pide corregir el contrato antes de programar. No necesitas provocar un fallo en el código para enseñar el problema.

### Minutos 40-60: delegación observable

Guía el ejercicio 3 y proyecta las ejecuciones de especialistas. Solicita un informe de trabajo real, no un diálogo teatral entre nueve nombres en una sola respuesta.

Observa cómo Squad decide los responsables y el orden de ejecución a partir de los charters y del plan aprobado. Comprueba que acuerda las interfaces antes de que otros trabajos dependan de ellas, mantiene un escritor por archivo y distingue las tareas independientes de las que deben esperar. No prescribas tú qué arquetipo debe ir primero ni cuál debe editar cada archivo.

Para cada delegación mostrada, pide identificar el miembro elegido, la responsabilidad de su charter que motivó la selección y la evidencia de la ejecución. Si el coordinador hace todo sin delegar, solicita que aplique el routing sin nombrar un especialista; si hay una limitación de la interfaz, regístrala en lugar de simular miembros.

En el minuto 55 comprueba que cada mesa tiene una ruta de ejecución. Si se atasca, usa tu repositorio de la etapa de implementación y pasa a revisar, anotando que ese tramo fue observado.

Cuando el código esté terminado, cada mesa ejecuta la alternativa de su lenguaje en el paso 2 del ejercicio 3 desde la raíz de práctica y comprueba el resultado en el paso 3. No adelantes estos comandos mientras falten archivos o solo exista la plantilla .NET.

### Minutos 60-72: revisión y evidencia

Guía el ejercicio 4. Ejecuta al menos un flujo feliz y los errores de título vacío e ID inexistente. Enseña la salida real del runner y evita confundir «cero pruebas» o la prueba vacía de xUnit con éxito.

Encarga la revisión y las comprobaciones a Squad mediante peticiones genéricas; observa qué revisores elige y si su selección se justifica con los charters. Las reparaciones se autorizan por hallazgo y alcance, no asignándolas a un miembro concreto.

Muestra un caso de archivo corrupto en el directorio temporal de una prueba, no dañando los datos de alguien. Si hay un hallazgo, acepta una reparación pequeña y repite las pruebas. Si no lo hay, explica qué defecto previene una prueba existente.

La revisión de agentes es una capa adicional. Los permisos, los checks y la persona siguen siendo necesarios. No describas directivas de Markdown como un sandbox ni prometas que todos los hooks del SDK se aplican automáticamente en cualquier interfaz.

### Minutos 72-82: continuidad sin la conversación

Guía el ejercicio 5. Cierra la actividad de escritura del editor antes de iniciar la sesión CLI. No repitas el contrato: pide recuperar decisiones y comprobar los archivos citados.

Si falta algo, revisa el inbox y el estado del escriba. Enseña cómo detectar una decisión no consolidada o equivocada. Nunca presentes una reconstrucción plausible del modelo como memoria verificada.

### Minutos 82-97: modelos por agente y evidencia

Guía el [ejercicio 6](04%20-%20ejercicios.md#ejercicio-6-agentes-con-distintos-modelos-en-copilot-cli) desde GitHub Copilot CLI, no desde el shell interactivo `squad`. Squad elige dos revisores según sus charters; la persona comprueba los IDs y asigna dos modelos disponibles en su cuenta. Conserva la propuesta aprobada para adjuntarla tras reiniciar la sesión y evita que un override de tarea oculte las preferencias persistentes.

Ensaya la configuración, las llamadas de lanzamiento y los metadatos que tu versión de CLI exponga. Proyecta por separado el modelo guardado en JSON, el solicitado por la herramienta y el reportado por el runtime; una respuesta del coordinador o un nombre de modelo dentro del prompt no acredita el modelo efectivo. Si los metadatos no están disponibles, registra «no expuesto»; si ambos modelos caen en el mismo fallback, no declares ejecución con modelos distintos.

Explica la limitación documentada de Squad 1.1.0 en VS Code: modelo de sesión compartido, no selección distinta por lanzamiento. No garantices esa distinción en todas las versiones futuras. Si falta acceso a dos modelos o selección por lanzamiento, utiliza pareja o evidencias reales del ensayo; no exijas compras ni habilites cargos. Revisa los dos informes y restaura únicamente las preferencias modificadas.

### Minutos 97-105: cerrar con criterio

Pide las evidencias del ejercicio y aplica la rúbrica. Recuerda que los archivos nuevos no aparecen completos en `git diff`.

Cierra con tres preguntas: «¿Qué no delegarías?», «¿Qué revisarías en una decisión guardada?» y «¿Cuándo un único asistente sería suficiente?». No dediques el cierre a instalar herramientas ni a nuevas funciones.

## Contingencias

| Situación | Respuesta en el taller |
| :--- | :--- |
| Sin acceso o sin cuota | Pareja con cuenta habilitada; después demostración y revisión de archivos |
| Caída de Internet | Utiliza etapas locales ya preparadas; marca la delegación como observada previamente |
| Instalación rota | No consumir los 105 minutos reparando; usar pareja y continuar la revisión |
| Nombres o estructura diferentes | Mostrar el mapeo real; conservar los nueve roles |
| Agente amplía alcance | Pausar, mostrar el contrato y volver a una tarea acotada |
| Dos agentes pisan un archivo | Detener escrituras, inspeccionar el diff y pedir a Squad que elija un único propietario según los charters |
| Memoria contiene un error | Aprobar una corrección explícita y comprobar su recuperación posterior |
| Solo un modelo disponible o sin selección por lanzamiento | Pareja o demostración ensayada; no simular dos modelos ni certificar ejecuciones no realizadas |
| El runtime no expone el modelo usado | Separar configuración y solicitud de modelo efectivo no confirmado |
| .NET restaura paquetes en directo | Usar la etapa local preparada y corregir la preparación para la próxima edición |
| Falta tiempo para programar | Pasar a implementación ensayada sin omitir revisión ni recuperación de memoria |

No existe sustitución offline para ejecutar los modelos de Copilot en esta práctica. Las copias locales permiten revisar y ejecutar la aplicación; no simulan una llamada real al servicio.

## Rúbrica de salida

| Dimensión | Evidencia aceptable |
| :--- | :--- |
| Equipo | Cuatro base y cinco arquetipos identificados en archivos reales |
| Delegación | Petición genérica, miembro elegido por Squad, justificación en su charter y ejecución real inspeccionada |
| Funcionalidad | Añadir, listar, completar y volver a abrir |
| Calidad | Suite real con casos de aceptación y al menos un caso negativo mostrado |
| Memoria | Una decisión recuperada en otra sesión con referencia a su archivo |
| Modelos | Configuración y solicitud identificadas; modelos reportados contrastados o falta de evidencia declarada; preferencias restauradas |
| Criterio humano | Un límite de permisos y una decisión que no se delega |

Anota por dimensión si la persona ejecutó, trabajó en pareja u observó evidencia. No penalices una restricción de licencia como si fuera falta de comprensión; tampoco certifiques ejecución individual cuando no ocurrió.

## Después del taller

Solicita feedback sin recoger tokens ni información privada. Revisa las versiones y los enlaces antes de repetir la sesión. Propón como continuación opcional un filtro de pendientes, pero deja claro que no pertenece a los 105 minutos ni al contrato evaluado.
