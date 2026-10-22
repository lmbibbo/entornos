# Roles y Operaciones · Oficina

**Paso 4 del algoritmo** (`../agents.md` §4): cada rol con las operaciones que puede
ejecutar **con cada herramienta**. Es el detalle que las fichas de workspace resumen y
que los diagramas de actividad muestran en versión reducida: los diagramas listan dos
operaciones por rol para no saturar; este documento es la lista completa.

Regla que ordena todo el documento: **un rol modifica un artefacto únicamente a través
de una herramienta declarada**. Si una operación no tiene herramienta, no existe.

---

## 1. Catálogo de roles

| Rol | Qué hace | Dónde actúa | Transición |
| :--- | :--- | :--- | :--- |
| **DirectorDeArte** | Fija el territorio creativo y autoriza el pase de la pieza. No produce. | DireccionCreativa · SalaRevision · RelacionClientes | → `ParCreativo` durante la crítica |
| **CreativoSenior** | Explora, cura referencias y alimenta el concepto. | DireccionCreativa | → `DirectorDeArte` al aprobarse el rumbo |
| **EjecutivoDeCuenta** | Traduce el pedido y conduce la relación con el cliente. | DireccionCreativa · RelacionClientes | → `DirectorDeArte` al iniciar la defensa |
| **Cliente** | Rol externo: valida objetivos y comenta lo presentado. | DireccionCreativa · RelacionClientes | → `EjecutivoDeCuenta` al cerrar la ronda |
| **DisenadorGrafico** | Compone la pieza y resuelve las correcciones. | EstudioProduccion · SalaRevision | → `RevisorDeCalidad` al publicar versión |
| **Redactor** | Escribe y ajusta el copy sobre el documento compartido. | EstudioProduccion | → `DisenadorGrafico` al cerrar el texto |
| **MotionDesigner** | Anima transiciones y prepara el render. | EstudioProduccion | → `DisenadorGrafico` al terminar el render |
| **RevisorDeCalidad** | Aplica el estándar de entrega y registra objeciones. | SalaRevision | → `DirectorDeArte` al emitir veredicto |
| **ParCreativo** | Crítica cruzada: objeta la pieza que no produjo. | SalaRevision | → `RevisorDeCalidad` al registrarse la crítica |

---

## 2. Operaciones por rol y herramienta

### DirectorDeArte

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| BriefingCreativo | PizarraColaborativa | marcar el territorio; anotar restricciones; confirmar el rumbo | DocumentoConcepto |
| CuraduriaReferencias | TableroReferencias | elegir el territorio; definir el criterio; descartar referencias | TableroMoodboard |
| CoCreacionPieza | CanalVozEquipo | marcar el encuadre; aprobar la dirección visual; pedir ajustes en vivo | PiezaGrafica (lectura) |
| IteracionVersion | ComentariosAnclados | priorizar correcciones; dar el visto bueno; reabrir un ítem | PiezaGrafica |
| CriticaColectiva | VideoReunion | moderar la crítica; ceder la palabra; emitir el veredicto | RegistroCritica |
| ChecklistEntrega | VerificadorEntrega | aprobar la entrega; firmar el pase | ChecklistCalidad |
| PresentacionPropuesta | PresentadorSlides | defender la propuesta; ajustar el relato en vivo | PropuestaComercial |
| RondaFeedback | ComentariosPorHilo | aceptar o rechazar un comentario; responder objeciones | HiloFeedback |

### CreativoSenior

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| BriefingCreativo | ChatGeneral | formular preguntas creativas; anotar hallazgos; compartir enlaces | BriefingCampana (lectura) |
| CuraduriaReferencias | TableroReferencias | cargar referencias; agrupar por territorio; descartar lo que no encaja; comentar una referencia | TableroMoodboard |

### EjecutivoDeCuenta

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| BriefingCreativo | VideoReunion | traducir el pedido; conducir la ronda de preguntas; cerrar acuerdos | BriefingCampana |
| CuraduriaReferencias | ForoHilosCreativos | verificar el encaje con el brief; marcar faltantes; responder dudas | TableroMoodboard (lectura) |
| PresentacionPropuesta | VideoReunion | conducir la presentación; registrar objeciones; cerrar el acuerdo | PropuestaComercial |
| RondaFeedback | ComentariosPorHilo | ordenar el feedback; derivar correcciones; confirmar el cierre | HiloFeedback |

### Cliente

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| BriefingCreativo | VideoReunion | validar objetivos y alcance; responder preguntas del brief | BriefingCampana (lectura) |
| PresentacionPropuesta | VideoReunion | plantear objeciones; manifestar acuerdo | PropuestaComercial (lectura) |
| RondaFeedback | PortalCliente | comentar la pieza; marcar aprobaciones; descargar la propuesta | ActaAprobacion |

### DisenadorGrafico

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| CoCreacionPieza | EditorGraficoColaborativo | componer la pieza base; integrar capas y estilos; bloquear una capa | PiezaGrafica |
| IteracionVersion | RepositorioVersiones | publicar una nueva versión; restaurar una versión; comparar versiones | PiezaGrafica |
| IteracionVersion | ComentariosAnclados | resolver un comentario; responder un comentario | PiezaGrafica |
| ChecklistEntrega | ComentariosAnclados | corregir los ítems marcados; repasar la pieza; marcar un ítem como resuelto | PiezaEnRevision |

### Redactor

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| CoCreacionPieza | EditorTextoCompartido | escribir el copy; ajustar titulares; comentar un párrafo | GuionCopy |
| IteracionVersion | RepositorioVersiones | corregir los textos observados; versionar el copy | GuionCopy |

### MotionDesigner

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| CoCreacionPieza | EditorGraficoColaborativo | animar transiciones; previsualizar el render; exportar el paquete | PiezaGrafica · PaqueteExportacion |

### RevisorDeCalidad

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| CriticaColectiva | ChatGeneral | registrar objeciones; verificar estándares; citar el checklist | RegistroCritica |
| ChecklistEntrega | VerificadorEntrega | aplicar el checklist; abrir correcciones; cerrar ítems | ChecklistCalidad |
| ChecklistEntrega | ComentariosAnclados | señalar el punto exacto; responder al diseñador | PiezaEnRevision |

### ParCreativo

| Actividad | Herramienta | Operaciones | Artefacto |
| :--- | :--- | :--- | :--- |
| CriticaColectiva | PizarraAnotaciones | objetar la pieza; marcar zonas; proponer ajustes concretos | PiezaEnRevision |

---

## 3. Vista por actividad

| Actividad | Workspace | Tipo | Roles y herramienta |
| :--- | :--- | :--- | :--- |
| BriefingCreativo | DireccionCreativa | sincrónica | EjecutivoDeCuenta (VideoReunion) · Cliente (VideoReunion) · DirectorDeArte (PizarraColaborativa) · CreativoSenior (ChatGeneral) |
| CuraduriaReferencias | DireccionCreativa | asincrónica | CreativoSenior (TableroReferencias) · DirectorDeArte (TableroReferencias) · EjecutivoDeCuenta (ForoHilosCreativos) |
| CoCreacionPieza | EstudioProduccion | sincrónica | DisenadorGrafico (EditorGraficoColaborativo) · Redactor (EditorTextoCompartido) · MotionDesigner (EditorGraficoColaborativo) · DirectorDeArte (CanalVozEquipo) |
| IteracionVersion | EstudioProduccion | asincrónica | DisenadorGrafico (RepositorioVersiones, ComentariosAnclados) · Redactor (RepositorioVersiones) · DirectorDeArte (ComentariosAnclados) |
| CriticaColectiva | SalaRevision | sincrónica | DirectorDeArte (VideoReunion) · ParCreativo (PizarraAnotaciones) · RevisorDeCalidad (ChatGeneral) |
| ChecklistEntrega | SalaRevision | asincrónica | RevisorDeCalidad (VerificadorEntrega, ComentariosAnclados) · DisenadorGrafico (ComentariosAnclados) · DirectorDeArte (VerificadorEntrega) |
| PresentacionPropuesta | RelacionClientes | sincrónica | EjecutivoDeCuenta (VideoReunion) · DirectorDeArte (PresentadorSlides) · Cliente (VideoReunion) |
| RondaFeedback | RelacionClientes | asincrónica | Cliente (PortalCliente) · EjecutivoDeCuenta (ComentariosPorHilo) · DirectorDeArte (ComentariosPorHilo) |

---

## 4. Reglas que este documento verifica

| Regla CSSL | Cómo se cumple |
| :--- | :--- |
| Operación → herramienta | Ninguna fila de la sección 2 existe sin herramienta declarada en el workspace. |
| Alineación temporal | Cada herramienta usada en una sesión coincide con su tipo (sincrónica/asincrónica). |
| Regla de oro | Toda actividad de la sección 3 tiene al menos un canal de comunicación. |
| Rol declarado | Un rol solo aparece en actividades de un workspace donde la ficha lo declara. |
| Visibilidad | El Cliente nunca opera sobre `PiezaGrafica` ni `PiezaEnRevision`; entra por `PortalCliente`. |

Los diagramas de `diagramas/02-actividades.drawio` muestran la estructura de cada
actividad: workspace, herramientas, actividad con protocolo y objetos, y roles con su
multiplicidad. Las operaciones no se dibujan; la lista completa es la sección 2 de
este documento.

---

## 5. Pendiente en este documento

Los pasos 6 y 7 del algoritmo agregan secciones a este mismo archivo:

- **Paso 6 — proceso:** qué acciones ejecuta cada rol para moverse entre actividades.
- **Paso 7 — protocolo:** qué acciones ejecuta cada rol dentro de cada estado de la sesión.
