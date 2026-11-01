# Temario del taller

## Objetivo

En 105 minutos configurarás un equipo de Squad, delegarás una aplicación pequeña y comprobarás sus resultados, incluida la selección de modelos por agente en Copilot CLI. El objetivo es aprender a dirigir agentes, no dominar Python o C# ni crear un sistema de producción.

La instalación y las descargas se completan antes del taller mediante la [preparación](01%20-%20preparacion.md). Si llegas sin el entorno listo, utiliza la modalidad por parejas u observación para no consumir la práctica instalando herramientas.

## Orden de trabajo

1. Antes de la sesión: sigue la preparación y la sección [Antes de la sesión: preparar el proyecto](04%20-%20ejercicios.md#antes-de-la-sesión-preparar-el-proyecto) de la guía integrada para comprobar el runtime, crear el repositorio e inicializar Squad. Revisa la lista de preparación y detente: todavía no configures el equipo ni construyas la aplicación.
2. Durante la sesión: sigue los [ejercicios](04%20-%20ejercicios.md) en orden. En el ejercicio 1 formas el equipo; en el 2 eliges el contexto técnico de Python o .NET y acuerdas el contrato; en el 3 autorizas la implementación y ejecutas la alternativa de tu proyecto.
3. Después de la primera ejecución: continúa con revisión y recuperación de memoria en los ejercicios 4 y 5; después contrasta los modelos por agente en el [ejercicio 6](04%20-%20ejercicios.md#ejercicio-6-agentes-con-distintos-modelos-en-copilot-cli) y termina con el cierre. Ejecutar una vez no sustituye estas comprobaciones.

Python y .NET son alternativas dentro de los mismos pasos, no guías independientes. Las acciones comunes de Squad se realizan una sola vez. Mantén la raíz del proyecto elegido al cambiar de interfaz.

## Agenda de 105 minutos

| Minutos | Duración | Actividad | Evidencia |
| :--- | ---: | :--- | :--- |
| 00-08 | 8 | Un asistente frente a un equipo; contexto y responsabilidad | Explicar cuándo no usar Squad |
| 08-15 | 7 | Comprobación de acceso y demostración VS Code/CLI | Squad visible o alternativa asignada |
| 15-30 | 15 | Ejercicio 1: formar y ampliar el equipo | Cuatro roles base y cinco extras |
| 30-40 | 10 | Ejercicio 2: acordar contrato y límites | Especificación y decisión persistente |
| 40-60 | 20 | Ejercicio 3: delegar la implementación | Aplicación y pruebas ejecutables |
| 60-72 | 12 | Ejercicio 4: revisar y corregir | Casos negativos y revisión humana |
| 72-82 | 10 | Ejercicio 5: recuperar memoria en otra interfaz | Decisión recuperada desde archivos |
| 82-97 | 15 | Ejercicio 6: agentes con distintos modelos en CLI | Configuración, solicitud y reporte del runtime contrastados |
| 97-105 | 8 | Cierre, evidencias y preguntas | Lista de salida y reflexión |

## Ideas que explicaremos

- Agente: una ejecución del modelo con instrucciones, contexto y herramientas
- Coordinador: selecciona especialistas según sus charters y el routing, ordena dependencias y reúne los resultados
- Context Engineering: elegir qué información recibe cada ejecución y cuándo
- Charter: identidad, responsabilidades y límites de un miembro
- Memoria: archivos que futuras ejecuciones leen; no entrenamiento del modelo
- Directiva: una regla expresada en lenguaje natural, no una garantía de seguridad
- Verificación: ejecutar comprobaciones y revisar resultados, no aceptar una afirmación del agente
- Modelo por agente: una preferencia persistente que debe contrastarse con el lanzamiento y el reporte del runtime; su aplicación depende de la interfaz

## Dos tecnologías, un contrato

| Capacidad | Python | C# |
| :--- | :--- | :--- |
| Interfaz | Consola con argumentos | Consola con argumentos |
| Añadir, listar y completar | Sí | Sí |
| Persistencia | JSON con biblioteca estándar | JSON con System.Text.Json |
| Pruebas | unittest | xUnit con dotnet test |
| Datos y errores | Mismo contrato | Mismo contrato |
| Infraestructura externa o en la nube | Ninguna | Ninguna |

En cada paso técnico, el participante elige la alternativa que corresponde al proyecto con el que trabaja. No tiene que instalar ambos runtimes ni construir una integración entre ellos. Si practica los dos lenguajes, usa repositorios separados.

## Equipo del taller

Squad propone equipos según el proyecto; con cuatro miembros universales especiales propios de la herramienta que siempre estarán presentes.

Añadimos cinco arquetipos distintos, no cinco nombres para el mismo trabajo. Los nombres Marvel son una ayuda mnemotécnica; la responsabilidad y los archivos del equipo son la referencia. Puedes usar los siguientes nombres como guía, e incluso si lo deseas, utilizar otras referencias como el programa de televisión Friends, Los Simpson o cualquier otra serie o franquicia que te resulte afín.

| Grupo | Nombre | Arquetipo | Responsabilidad |
| :--- | :--- | :--- | :--- |
| Base | Captain America | Lead | Contrato técnico, dependencias y revisión final |
| Base | Iron Man | Backend | Lógica de tareas y comandos |
| Base | Spider-Man | Frontend / experiencia de consola | Ayuda, mensajes y presentación |
| Base | Black Widow | Tester | Pruebas de comportamiento y regresión |
| Extra 1 | Captain Marvel | Producto | Historias, alcance y criterios de aceptación |
| Extra 2 | Vision | Persistencia | Esquema JSON, lectura y escritura segura |
| Extra 3 | Doctor Strange | Seguridad | Rutas, datos sensibles y entradas inválidas |
| Extra 4 | Ms. Marvel | Documentación | Guía de uso y evidencias de decisiones |
| Extra 5 | Shuri | Portabilidad | Comandos reproducibles en PowerShell 7 y Bash |

Son nueve especialistas, además del coordinador y los miembros operativos que cree Squad, como Scribe o Ralph. Estos últimos no cuentan entre los cinco extras. No es necesario mantener nueve ejecuciones activas: activaremos solo el rol adecuado y como máximo dos trabajos independientes a la vez.

## Criterios de salida

- [ ] Distingo los cuatro roles base de los cinco especialistas adicionales
- [ ] Localizo el roster, el routing y al menos una decisión compartida
- [ ] Formulo una petición sin nombres de miembros y compruebo cómo Squad justifica su reparto con los charters
- [ ] Puedo añadir, listar y completar una tarea, o revisar esa evidencia en pareja
- [ ] Compruebo al menos un error y la persistencia tras reiniciar
- [ ] Ejecuto las pruebas, o registro quién las ejecutó y qué resultado obtuvo
- [ ] Recupero una decisión en una sesión nueva sin volver a explicarla
- [ ] Distingo modelo configurado, solicitado y reportado; identifico las limitaciones de mi interfaz y restauro las preferencias anteriores
- [ ] Identifico una decisión que debe seguir tomando la persona

La finalización en modalidad de observación se registra como tal. No equivale a haber ejecutado todos los agentes en la cuenta propia.
