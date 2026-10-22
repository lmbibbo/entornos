# Especificación de Espacios Colaborativos en CSSL (Collaborative Software System Language)
**Agencia Creativa sin Restricciones Tecnológicas**
**Fase 1: Configuración de Workspaces y Sesiones**

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
| **Objetos compartidos:** | BriefCampana (*brief_v01.pdf*), TableroMoodboard (*moodboard_v02.fig*), DocumentoConcepto (*concepto_v03.md*). |

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

## 3. Roles y Transiciones

El **detalle de operaciones por herramienta** —qué puede hacer cada rol con cada herramienta, actividad por actividad— está en [`roles.md`](roles.md). Esta sección resume el catálogo y las mutaciones de rol.

| Rol | Workspace | Operaciones | Herramienta habilitante | Transición |
| :--- | :--- | :--- | :--- | :--- |
| **DirectorDeArte** | DireccionCreativa · SalaRevision · RelacionClientes | Define el territorio creativo; aprueba el pase a entrega | PizarraColaborativa | → ParCreativo durante la crítica |
| **CreativoSenior** | DireccionCreativa | Propone conceptos; cura referencias por territorio | TableroReferencias | → DirectorDeArte al aprobarse el rumbo |
| **EjecutivoDeCuenta** | DireccionCreativa · RelacionClientes | Traduce el brief; conduce la presentación | VideoReunion | → DirectorDeArte al iniciar la defensa |
| **Cliente** | DireccionCreativa · RelacionClientes | Valida objetivos; comenta la propuesta | PortalCliente | → EjecutivoDeCuenta al cerrar la ronda |
| **DisenadorGrafico** | EstudioProduccion · SalaRevision | Compone la pieza; corrige observaciones | EditorGraficoColaborativo | → RevisorDeCalidad al publicar versión |
| **Redactor** | EstudioProduccion | Escribe el copy; ajusta titulares | EditorTextoCompartido | → DisenadorGrafico al cerrar el texto |
| **MotionDesigner** | EstudioProduccion | Anima transiciones; exporta el paquete | EditorGraficoColaborativo | → DisenadorGrafico al terminar el render |
| **RevisorDeCalidad** | SalaRevision | Aplica el checklist; registra objeciones | VerificadorEntrega | → DirectorDeArte al emitir veredicto |
| **ParCreativo** | SalaRevision | Critica la pieza; propone ajustes concretos | ComentariosAnclados | → RevisorDeCalidad al registrarse la crítica |

### Transiciones

| Desde | Hacia | Disparador | Efecto |
| :--- | :--- | :--- | :--- |
| CreativoSenior | DirectorDeArte | Se aprueba el rumbo | El concepto pasa a producción |
| DisenadorGrafico | RevisorDeCalidad | Se publica una versión | Se abre la revisión formal |
| RevisorDeCalidad | DirectorDeArte | Se cierra la crítica | Veredicto de pase o retorno |
| DirectorDeArte | ParCreativo | Comienza la crítica de su propia pieza | Evita el sesgo de autoría |
| Cliente | EjecutivoDeCuenta | Termina la ronda de feedback | El pedido vuelve al estudio |

---

## 4. Awareness

Declarado según [`../awareness.md`](../awareness.md), atado a un espacio o a una actividad.

| Alcance | Elemento | Pregunta que resuelve | Nivel |
| :--- | :--- | :--- | :--- |
| Actividad `BriefingCreativo` | `Presence` | ¿Quiénes están en esta sesión? | Sesión |
| Espacio `DireccionCreativa` | `Density` | ¿Qué densidad de usuarios hay en la sala? | Espacio |
| Actividad `CuraduriaReferencias` | `Changes` | ¿Qué referencias cambiaron desde mi última visita? | Artefacto |
| Actividad `CoCreacionPieza` | `ObjectsUsers` | ¿Quién está editando qué capa? | Artefacto |
| Actividad `IteracionVersion` | `Changes` | ¿Qué cambió desde la última versión? | Artefacto |
| Actividad `CriticaColectiva` | `Changes` | ¿Qué se corrigió desde la última crítica? | Artefacto |
| Actividad `ChecklistEntrega` | `ObjectHistory` | ¿Quién hizo cada cambio? | Artefacto |
| Actividad `PresentacionPropuesta` | `UserAction` | ¿Qué está haciendo el cliente durante la presentación? | Sesión |
| Actividad `RondaFeedback` | `Visibility` | ¿Qué puede ver el cliente? | Artefacto |

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
