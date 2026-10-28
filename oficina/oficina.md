# Especificación de Espacios Colaborativos en CSSL (Collaborative Software System Language)
**Agencia Creativa sin Restricciones Tecnológicas**
**Fases 1–4: workspaces, sesiones, awareness, proceso y protocolo**

> Diseño completo. Los diagramas están en [`diagramas/`](diagramas/).

---

## 1. Definición del Entorno de Oficina
El sistema colaborativo de la agencia se descompone en 4 espacios de trabajo independientes (Workspaces) que cubren el ciclo de una pieza sin superponerse: **concepto → producción → revisión interna → aprobación del cliente**. Cada espacio tiene roles, dinámica social y foco de awareness propios.

---

## 2. Fichas técnicas de Workspace (Sintaxis Concreta CSSL)

En las fichas, `↔` marca la herramienta que hace de **canal de comunicación** en esa sesión; el resto son herramientas de producción.

### Ficha de Workspace 1: Mesa de Dirección Creativa

| Información General: | |
| :--- | :--- |
| **Nombre:** | DireccionCreativa |
| **Descripción:** | Mesa donde el pedido se convierte en territorio creativo: concepto, referencias y rumbo de la campaña. Es el espacio de decisión, no de ejecución. |
| **Información Detallada:** | Se entra con un brief y se sale con un rumbo aprobado. La autoridad es del DirectorDeArte; el cliente participa solo en la instancia sincrónica. |
| **Sesiones:** | 1. **BriefingCreativo:** Sesión sincrónica de lectura conjunta del pedido, preguntas al cliente y fijación de objetivos.<br>2. **CuraduriaReferencias:** Sesión asincrónica de construcción del tablero de referencias y exploración de territorios visuales. |
| **Herramientas:** | ↔ VideoReunion (sincrónica), PizarraColaborativa (sincrónica), ↔ ChatGeneral (sincrónica), TableroReferencias (asincrónica), ↔ ForoHilosCreativos (asincrónica). |
| **Roles:** | DirectorDeArte, CreativoSenior, EjecutivoDeCuenta, Cliente. |
| **Awareness:** | `Presence` (nivel sesión): ¿quiénes están en la mesa? · `Density` (nivel espacio): ¿qué densidad de usuarios hay en la sala? |
| **Objetos compartidos:** | BriefingCampana (*brief_v01.pdf*), TableroMoodboard (*moodboard_v02.fig*), DocumentoConcepto (*concepto_v03.md*). |

<br>

### Ficha de Workspace 2: Estudio de Producción

| Información General: | |
| :--- | :--- |
| **Nombre:** | EstudioProduccion |
| **Descripción:** | Taller de ejecución: piezas gráficas, copy y motion sobre lienzos compartidos, con versionado y comentarios anclados. |
| **Información Detallada:** | Es el único espacio donde se modifica la pieza. El trabajo es simultáneo sobre el mismo lienzo, con roles que se alternan según la capa activa. |
| **Sesiones:** | 1. **CoCreacionPieza:** Sesión sincrónica de edición simultánea de la pieza con el equipo completo.<br>2. **IteracionVersion:** Sesión asincrónica de ajustes sobre versiones y resolución de comentarios anclados. |
| **Herramientas:** | EditorGraficoColaborativo (sincrónica), EditorTextoCompartido (sincrónica), ↔ CanalVozEquipo (sincrónica), RepositorioVersiones (asincrónica), ↔ ComentariosAnclados (asincrónica). |
| **Roles:** | DisenadorGrafico, Redactor, MotionDesigner, DirectorDeArte. |
| **Awareness:** | `ObjectsUsers` (nivel artefacto): ¿quién está editando qué capa? · `Changes` (nivel artefacto): ¿qué cambió desde la última versión? |
| **Objetos compartidos:** | PiezaGrafica (*pieza_v04.fig*), GuionCopy (*copy_v02.doc*), PaqueteExportacion (*assets_v04.zip*). |

<br>

### Ficha de Workspace 3: Sala de Revisión

| Información General: | |
| :--- | :--- |
| **Nombre:** | SalaRevision |
| **Descripción:** | Sala de crítica: la pieza se somete a revisión cruzada y control de calidad antes de salir del estudio. |
| **Información Detallada:** | Nadie aprueba su propia pieza. El DirectorDeArte modera y delega la crítica en el ParCreativo para evitar el sesgo de autoría. |
| **Sesiones:** | 1. **CriticaColectiva:** Sesión sincrónica de revisión en vivo con la pieza proyectada y las objeciones registradas.<br>2. **ChecklistEntrega:** Sesión asincrónica de verificación contra el brief y los estándares de entrega. |
| **Herramientas:** | ↔ VideoReunion (sincrónica), PizarraAnotaciones (sincrónica), ↔ ChatGeneral (sincrónica), VerificadorEntrega (asincrónica), ↔ ComentariosAnclados (asincrónica). |
| **Roles:** | DirectorDeArte, RevisorDeCalidad, ParCreativo, DisenadorGrafico. |
| **Awareness:** | `Changes` (nivel artefacto): ¿qué se corrigió desde la última crítica? · `ObjectHistory` (nivel artefacto): ¿quién hizo cada cambio? |
| **Objetos compartidos:** | RegistroCritica (*critica_v01.md*), ChecklistCalidad (*checklist_v01.md*), PiezaEnRevision (*pieza_v04.fig*). |

<br>

### Ficha de Workspace 4: Frente de Clientes

| Información General: | |
| :--- | :--- |
| **Nombre:** | RelacionClientes |
| **Descripción:** | Frente con el cliente: presentación de propuestas, rondas de feedback y aprobación formal. Lo que el cliente ve se decide acá. |
| **Información Detallada:** | Es el único espacio con un rol externo. La visibilidad es la restricción central: el cliente solo accede a lo presentado, nunca al estudio en producción. |
| **Sesiones:** | 1. **PresentacionPropuesta:** Sesión sincrónica de defensa de la propuesta y relevamiento de objeciones en vivo.<br>2. **RondaFeedback:** Sesión asincrónica de comentarios del cliente sobre la pieza presentada. |
| **Herramientas:** | ↔ VideoReunion (sincrónica), PresentadorSlides (sincrónica), ↔ ChatGeneral (sincrónica), PortalCliente (asincrónica), ↔ ComentariosPorHilo (asincrónica). |
| **Roles:** | EjecutivoDeCuenta, Cliente, DirectorDeArte. |
| **Awareness:** | `Visibility` (nivel artefacto): ¿qué puede ver el cliente? · `UserAction` (nivel sesión): ¿qué está haciendo el cliente en el portal? |
| **Objetos compartidos:** | PropuestaComercial (*propuesta_v02.pdf*), HiloFeedback (*feedback_cliente.md*), ActaAprobacion (*aprobacion_v01.pdf*). |

---

## 3. Roles por workspace

El catálogo completo —propósito, tipo, asignación por actividad, matriz de operaciones y
transiciones— está en [`roles.md`](roles.md). Esta sección solo indexa qué roles
participan en cada workspace; no duplica la matriz.

| Workspace | Roles |
| :--- | :--- |
| DireccionCreativa | DirectorDeArte · CreativoSenior · EjecutivoDeCuenta · Cliente |
| EstudioProduccion | DisenadorGrafico · Redactor · MotionDesigner · DirectorDeArte |
| SalaRevision | DirectorDeArte · RevisorDeCalidad · ParCreativo · DisenadorGrafico |
| RelacionClientes | EjecutivoDeCuenta · Cliente · DirectorDeArte |

Las transiciones y su ámbito (`proceso` o `protocolo`) están en [`roles.md`](roles.md)
§4; el proceso, en [`proceso.md`](proceso.md); los protocolos por actividad, en
[`roles.md`](roles.md) §6.

---

## 4. Awareness

Declarado según [`../awareness.md`](../awareness.md), atado a un espacio, una actividad,
el proceso o un protocolo. Las fichas de workspace resumen los dos elementos principales
de cada espacio; esta tabla es la declaración completa.

| Alcance | Elemento | Pregunta que resuelve | Nivel | Dónde se muestra | Fuente de datos |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Espacio `DireccionCreativa` | `Density` | ¿Qué densidad de usuarios hay en la sala? | Espacio | Contador en el encabezado del workspace | Presencia agregada por sala |
| Espacio `EstudioProduccion` | `ActivityLevel` | ¿Qué nivel de actividad tiene el estudio? | Espacio | Indicador de actividad en la barra del workspace | Eventos de edición por sesión |
| Espacio `SalaRevision` | `PlaceAction` | ¿Qué acción se está haciendo en la sala? | Espacio | Etiqueta de estado en la cabecera | Estado de la sesión activa |
| Espacio `RelacionClientes` | `UserLocation` | ¿En qué parte del frente está el cliente? | Espacio | Mapa de presencia del portal | Presencia por sesión y portal |
| Actividad `BriefingCreativo` | `Presence` | ¿Quiénes están en esta sesión? | Sesión | Avatares en la barra de la reunión | Presencia de la sesión |
| Actividad `BriefingCreativo` | `Rol` | ¿Qué rol ejerce cada participante? | Sesión | Badge de rol junto al avatar | Asignación de roles.md §2 |
| Actividad `CuraduriaReferencias` | `Changes` | ¿Qué referencias cambiaron desde mi última visita? | Artefacto | Resaltado de tarjetas nuevas | Metadatos del tablero |
| Actividad `CuraduriaReferencias` | `Objects` | ¿En qué estado está el tablero? | Artefacto | Contador de referencias por territorio | Estado del tablero |
| Actividad `CoCreacionPieza` | `ObjectsUsers` | ¿Quién está editando qué capa? | Artefacto | Cursores con nombre sobre el lienzo | Sesión del editor colaborativo |
| Actividad `CoCreacionPieza` | `Rol` | ¿Quién actúa como diseñador, redactor o motion en cada capa? | Artefacto | Etiqueta de rol en el cursor y en la capa | Asignación de roles.md §2 y capa activa |
| Actividad `IteracionVersion` | `Changes` | ¿Qué cambió desde la última versión? | Artefacto | Diff resumido en la lista de versiones | Comparación de versiones |
| Actividad `IteracionVersion` | `Objects` | ¿Qué versión está publicada y cuál es la vigente? | Artefacto | Insignia «vigente» en el repositorio | Estado de las versiones |
| Actividad `CriticaColectiva` | `Changes` | ¿Qué se corrigió desde la última crítica? | Artefacto | Lista de cambios frente al registro anterior | Registro de crítica y versiones |
| Actividad `CriticaColectiva` | `Rol` | ¿Quién habla como autor y quién como par crítico? | Sesión | Turno y badge en la sala | Estado del protocolo y asignación |
| Actividad `ChecklistEntrega` | `ObjectHistory` | ¿Quién hizo cada cambio? | Artefacto | Historial por ítem del checklist | Metadatos de la pieza y del checklist |
| Actividad `ChecklistEntrega` | `Objects` | ¿En qué estado está el checklist? | Artefacto | Semáforo de ítems abiertos y cerrados | Estado del verificador |
| Actividad `PresentacionPropuesta` | `UserAction` | ¿Qué está haciendo el cliente durante la presentación? | Sesión | Indicador de actividad en la sala | Eventos del cliente en la reunión |
| Actividad `PresentacionPropuesta` | `Expectations` | ¿Qué se espera que haga el cliente después de cada objeción? | Sesión | Indicador «siguiente paso» en la barra | Estado del protocolo y objeciones abiertas |
| Actividad `RondaFeedback` | `Visibility` | ¿Qué puede ver el cliente? | Artefacto | Candado y alcance en el portal | Permisos del portal |
| Actividad `RondaFeedback` | `ObjectsUsers` | ¿Quién está leyendo o comentando la pieza? | Artefacto | Avatares en el hilo y en la pieza | Presencia del portal y comentarios |
| Proceso | `UserHistory` | ¿Qué actividades completó ya el pedido? | Entorno | Línea de tiempo del pedido en el panel de proceso | Historial de transiciones `PR-` (proceso.md §3) |
| Proceso | `Expectations` | ¿Qué actividad sigue y qué se espera del rol? | Entorno | Indicador «próximo paso» en el panel del pedido | Estado del proceso y guardas de proceso.md §3 |
| Proceso | `ActivityLevel` | ¿Dónde está el cuello de botella del proceso? | Entorno | Mapa de calor por actividad en el tablero de proceso | Tiempo en estado y transiciones `PR-` |
| Protocolo | `Rol` | ¿En qué paso del protocolo está cada participante y con qué rol? | Sesión | Badge de rol y paso actual en la barra de la sesión | Estado del protocolo `PT-` (roles.md §6) |
| Protocolo | `PlaceAction` | ¿Qué operación está habilitada ahora en esta sesión? | Sesión | Resaltado del control habilitado en la herramienta | Estado del protocolo y permisos |
| Protocolo | `Expectations` | ¿Qué se espera de mí en este paso? | Sesión | Indicador «te toca» en la lista de participantes | Estado del protocolo y rol activo |

Los cuatro alcances quedan cubiertos. `Proceso` y `Protocolo` no agregan elementos
nuevos al catálogo: reutilizan `UserHistory`, `Expectations`, `ActivityLevel`, `Rol`,
`PlaceAction` y `ObjectsUsers` en el nivel que corresponde.

---

## 5. Convenciones y Orden de Trabajo

### Convenciones de nombres

| Elemento | Convención | Ejemplo |
| :--- | :--- | :--- |
| Workspace | PascalCase sin espacios ni acentos | `DireccionCreativa` |
| Sesión | PascalCase | `BriefingCreativo` |
| Herramienta | PascalCase que indique función | `EditorGraficoColaborativo` |
| Rol | PascalCase en singular | `DirectorDeArte` |
| Objeto compartido | PascalCase + archivo en cursiva | `BriefingCampana` (*brief_v01.pdf*) |
| Diagrama | `NN-nombre.drawio`, lienzo 1600×900 | `01-mapa-workspaces.drawio` |

### Reglas que no se negocian

- **Alineación temporal:** una sesión sincrónica solo admite herramientas sincrónicas; una asincrónica, herramientas asincrónicas.
- **Regla de oro:** toda actividad tiene al menos una herramienta de comunicación.
- **Operación → herramienta:** un rol solo modifica un artefacto a través de una herramienta declarada.
- **Sin pregunta no hay awareness:** cada declaración de la sección 4 responde a una pregunta de coordinación concreta.
