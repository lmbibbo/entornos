# Roles y Operaciones · Oficina

**Pasos 4 a 7 del algoritmo** (`../agents.md` §§4–7). Este archivo es la **fuente única**
de roles, asignación por actividad, operaciones, transiciones, proceso y protocolo del
proyecto. Las fichas de workspace resumen los roles y enlazan aquí; no duplican la matriz.

Regla que ordena todo el documento: **un rol modifica un artefacto únicamente a través
de una herramienta declarada**. Si una operación no tiene actividad, herramienta,
artefacto y modo, no existe.

Modos: `L` = lectura · `E` = escritura. En este proyecto todos los roles tienen
multiplicidad `1` en cada actividad; si el grupo cambia, se ajusta en §2.

---

## 1. Catálogo de roles

| Rol | Propósito | Tipo | Workspaces |
| :--- | :--- | :--- | :--- |
| **DirectorDeArte** | Fija el territorio creativo y autoriza el pase de la pieza. No produce. | interno | DireccionCreativa · SalaRevision · RelacionClientes |
| **CreativoSenior** | Explora, cura referencias y alimenta el concepto. | interno | DireccionCreativa |
| **EjecutivoDeCuenta** | Traduce el pedido y conduce la relación con el cliente. | interno | DireccionCreativa · RelacionClientes |
| **Cliente** | Rol externo: valida objetivos y comenta lo presentado. | externo | DireccionCreativa · RelacionClientes |
| **DisenadorGrafico** | Compone la pieza y resuelve las correcciones. | interno | EstudioProduccion · SalaRevision |
| **Redactor** | Escribe y ajusta el copy sobre el documento compartido. | interno | EstudioProduccion |
| **MotionDesigner** | Anima transiciones y prepara el render. | interno | EstudioProduccion |
| **RevisorDeCalidad** | Aplica el estándar de entrega y registra objeciones. | interno | SalaRevision |
| **ParCreativo** | Crítica cruzada: objeta la pieza que no produjo. | interno | SalaRevision |

---

## 2. Asignación rol-actividad

| Actividad | Workspace | Tipo | Rol | Multiplicidad | Herramienta(s) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| BriefingCreativo | DireccionCreativa | sincrónica | DirectorDeArte | `1` | PizarraColaborativa |
| BriefingCreativo | DireccionCreativa | sincrónica | CreativoSenior | `1` | ChatGeneral |
| BriefingCreativo | DireccionCreativa | sincrónica | EjecutivoDeCuenta | `1` | VideoReunion |
| BriefingCreativo | DireccionCreativa | sincrónica | Cliente | `1` | VideoReunion |
| CuraduriaReferencias | DireccionCreativa | asincrónica | CreativoSenior | `1` | TableroReferencias |
| CuraduriaReferencias | DireccionCreativa | asincrónica | DirectorDeArte | `1` | TableroReferencias |
| CuraduriaReferencias | DireccionCreativa | asincrónica | EjecutivoDeCuenta | `1` | ForoHilosCreativos |
| CoCreacionPieza | EstudioProduccion | sincrónica | DisenadorGrafico | `1` | EditorGraficoColaborativo |
| CoCreacionPieza | EstudioProduccion | sincrónica | Redactor | `1` | EditorTextoCompartido |
| CoCreacionPieza | EstudioProduccion | sincrónica | MotionDesigner | `1` | EditorGraficoColaborativo |
| CoCreacionPieza | EstudioProduccion | sincrónica | DirectorDeArte | `1` | CanalVozEquipo |
| IteracionVersion | EstudioProduccion | asincrónica | DisenadorGrafico | `1` | RepositorioVersiones |
| IteracionVersion | EstudioProduccion | asincrónica | DisenadorGrafico | `1` | ComentariosAnclados |
| IteracionVersion | EstudioProduccion | asincrónica | Redactor | `1` | RepositorioVersiones |
| IteracionVersion | EstudioProduccion | asincrónica | DirectorDeArte | `1` | ComentariosAnclados |
| CriticaColectiva | SalaRevision | sincrónica | DirectorDeArte | `1` | VideoReunion |
| CriticaColectiva | SalaRevision | sincrónica | ParCreativo | `1` | PizarraAnotaciones |
| CriticaColectiva | SalaRevision | sincrónica | RevisorDeCalidad | `1` | ChatGeneral |
| ChecklistEntrega | SalaRevision | asincrónica | RevisorDeCalidad | `1` | VerificadorEntrega |
| ChecklistEntrega | SalaRevision | asincrónica | RevisorDeCalidad | `1` | ComentariosAnclados |
| ChecklistEntrega | SalaRevision | asincrónica | DisenadorGrafico | `1` | ComentariosAnclados |
| ChecklistEntrega | SalaRevision | asincrónica | DirectorDeArte | `1` | VerificadorEntrega |
| PresentacionPropuesta | RelacionClientes | sincrónica | EjecutivoDeCuenta | `1` | VideoReunion |
| PresentacionPropuesta | RelacionClientes | sincrónica | DirectorDeArte | `1` | PresentadorSlides |
| PresentacionPropuesta | RelacionClientes | sincrónica | Cliente | `1` | VideoReunion |
| RondaFeedback | RelacionClientes | asincrónica | Cliente | `1` | PortalCliente |
| RondaFeedback | RelacionClientes | asincrónica | EjecutivoDeCuenta | `1` | ComentariosPorHilo |
| RondaFeedback | RelacionClientes | asincrónica | DirectorDeArte | `1` | ComentariosPorHilo |

---

## 3. Matriz de operaciones

`Dispara` referencia la transición cuyo disparador es la operación. Cada `TR-` tiene
exactamente una operación disparadora; las guardas y los efectos se detallan en
[`proceso.md`](proceso.md) y en §6.

| ID | Actividad | Rol | Herramienta | Artefacto | Modo | Operación | Dispara |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `OP-DIR-01` | BriefingCreativo | DirectorDeArte | PizarraColaborativa | DocumentoConcepto | `E` | marcar el territorio | — |
| `OP-DIR-02` | BriefingCreativo | DirectorDeArte | PizarraColaborativa | DocumentoConcepto | `E` | anotar restricciones | — |
| `OP-DIR-03` | BriefingCreativo | DirectorDeArte | PizarraColaborativa | DocumentoConcepto | `E` | confirmar el rumbo | — |
| `OP-DIR-04` | CuraduriaReferencias | DirectorDeArte | TableroReferencias | TableroMoodboard | `E` | elegir el territorio | `TR-01` |
| `OP-DIR-05` | CuraduriaReferencias | DirectorDeArte | TableroReferencias | TableroMoodboard | `E` | definir el criterio | — |
| `OP-DIR-06` | CuraduriaReferencias | DirectorDeArte | TableroReferencias | TableroMoodboard | `E` | descartar referencias | — |
| `OP-DIR-07` | CoCreacionPieza | DirectorDeArte | CanalVozEquipo | PiezaGrafica | `L` | marcar el encuadre | — |
| `OP-DIR-08` | CoCreacionPieza | DirectorDeArte | CanalVozEquipo | PiezaGrafica | `L` | aprobar la dirección visual | — |
| `OP-DIR-09` | CoCreacionPieza | DirectorDeArte | CanalVozEquipo | PiezaGrafica | `L` | pedir ajustes en vivo | — |
| `OP-DIR-10` | IteracionVersion | DirectorDeArte | ComentariosAnclados | PiezaGrafica | `E` | priorizar correcciones | — |
| `OP-DIR-11` | IteracionVersion | DirectorDeArte | ComentariosAnclados | PiezaGrafica | `E` | dar el visto bueno | `TR-02` |
| `OP-DIR-12` | IteracionVersion | DirectorDeArte | ComentariosAnclados | PiezaGrafica | `E` | reabrir un ítem | — |
| `OP-DIR-13` | CriticaColectiva | DirectorDeArte | VideoReunion | RegistroCritica | `E` | moderar la crítica | — |
| `OP-DIR-14` | CriticaColectiva | DirectorDeArte | VideoReunion | RegistroCritica | `E` | ceder la palabra | `TR-04` |
| `OP-DIR-15` | CriticaColectiva | DirectorDeArte | VideoReunion | RegistroCritica | `E` | emitir el veredicto | — |
| `OP-DIR-16` | ChecklistEntrega | DirectorDeArte | VerificadorEntrega | ChecklistCalidad | `E` | aprobar la entrega | — |
| `OP-DIR-17` | ChecklistEntrega | DirectorDeArte | VerificadorEntrega | ChecklistCalidad | `E` | firmar el pase | — |
| `OP-DIR-18` | PresentacionPropuesta | DirectorDeArte | PresentadorSlides | PropuestaComercial | `E` | defender la propuesta | — |
| `OP-DIR-19` | PresentacionPropuesta | DirectorDeArte | PresentadorSlides | PropuestaComercial | `E` | ajustar el relato en vivo | — |
| `OP-DIR-20` | RondaFeedback | DirectorDeArte | ComentariosPorHilo | HiloFeedback | `E` | aceptar o rechazar un comentario | — |
| `OP-DIR-21` | RondaFeedback | DirectorDeArte | ComentariosPorHilo | HiloFeedback | `E` | responder objeciones | — |
| `OP-CRE-01` | BriefingCreativo | CreativoSenior | ChatGeneral | BriefingCampana | `L` | formular preguntas creativas | — |
| `OP-CRE-02` | BriefingCreativo | CreativoSenior | ChatGeneral | BriefingCampana | `L` | anotar hallazgos | — |
| `OP-CRE-03` | BriefingCreativo | CreativoSenior | ChatGeneral | BriefingCampana | `L` | compartir enlaces | — |
| `OP-CRE-04` | CuraduriaReferencias | CreativoSenior | TableroReferencias | TableroMoodboard | `E` | cargar referencias | — |
| `OP-CRE-05` | CuraduriaReferencias | CreativoSenior | TableroReferencias | TableroMoodboard | `E` | agrupar por territorio | — |
| `OP-CRE-06` | CuraduriaReferencias | CreativoSenior | TableroReferencias | TableroMoodboard | `E` | descartar lo que no encaja | — |
| `OP-CRE-07` | CuraduriaReferencias | CreativoSenior | TableroReferencias | TableroMoodboard | `E` | comentar una referencia | — |
| `OP-EJE-01` | BriefingCreativo | EjecutivoDeCuenta | VideoReunion | BriefingCampana | `E` | traducir el pedido | — |
| `OP-EJE-02` | BriefingCreativo | EjecutivoDeCuenta | VideoReunion | BriefingCampana | `E` | conducir la ronda de preguntas | — |
| `OP-EJE-03` | BriefingCreativo | EjecutivoDeCuenta | VideoReunion | BriefingCampana | `E` | cerrar acuerdos | — |
| `OP-EJE-04` | CuraduriaReferencias | EjecutivoDeCuenta | ForoHilosCreativos | TableroMoodboard | `L` | verificar el encaje con el brief | — |
| `OP-EJE-05` | CuraduriaReferencias | EjecutivoDeCuenta | ForoHilosCreativos | TableroMoodboard | `L` | marcar faltantes | — |
| `OP-EJE-06` | CuraduriaReferencias | EjecutivoDeCuenta | ForoHilosCreativos | TableroMoodboard | `L` | responder dudas | — |
| `OP-EJE-07` | PresentacionPropuesta | EjecutivoDeCuenta | VideoReunion | PropuestaComercial | `E` | conducir la presentación | `TR-07` |
| `OP-EJE-08` | PresentacionPropuesta | EjecutivoDeCuenta | VideoReunion | PropuestaComercial | `E` | registrar objeciones | — |
| `OP-EJE-09` | PresentacionPropuesta | EjecutivoDeCuenta | VideoReunion | PropuestaComercial | `E` | cerrar el acuerdo | — |
| `OP-EJE-10` | RondaFeedback | EjecutivoDeCuenta | ComentariosPorHilo | HiloFeedback | `E` | ordenar el feedback | — |
| `OP-EJE-11` | RondaFeedback | EjecutivoDeCuenta | ComentariosPorHilo | HiloFeedback | `E` | derivar correcciones | — |
| `OP-EJE-12` | RondaFeedback | EjecutivoDeCuenta | ComentariosPorHilo | HiloFeedback | `E` | confirmar el cierre | — |
| `OP-CLI-01` | BriefingCreativo | Cliente | VideoReunion | BriefingCampana | `L` | validar objetivos y alcance | — |
| `OP-CLI-02` | BriefingCreativo | Cliente | VideoReunion | BriefingCampana | `L` | responder preguntas del brief | — |
| `OP-CLI-03` | PresentacionPropuesta | Cliente | VideoReunion | PropuestaComercial | `L` | plantear objeciones | — |
| `OP-CLI-04` | PresentacionPropuesta | Cliente | VideoReunion | PropuestaComercial | `L` | manifestar acuerdo | — |
| `OP-CLI-05` | RondaFeedback | Cliente | PortalCliente | HiloFeedback | `E` | comentar la pieza | — |
| `OP-CLI-06` | RondaFeedback | Cliente | PortalCliente | ActaAprobacion | `E` | marcar aprobaciones | `TR-05` |
| `OP-CLI-07` | RondaFeedback | Cliente | PortalCliente | PropuestaComercial | `L` | descargar la propuesta | — |
| `OP-DIS-01` | CoCreacionPieza | DisenadorGrafico | EditorGraficoColaborativo | PiezaGrafica | `E` | componer la pieza base | — |
| `OP-DIS-02` | CoCreacionPieza | DisenadorGrafico | EditorGraficoColaborativo | PiezaGrafica | `E` | integrar capas y estilos | — |
| `OP-DIS-03` | CoCreacionPieza | DisenadorGrafico | EditorGraficoColaborativo | PiezaGrafica | `E` | bloquear una capa | — |
| `OP-DIS-04` | IteracionVersion | DisenadorGrafico | RepositorioVersiones | PiezaGrafica | `E` | publicar una nueva versión | — |
| `OP-DIS-05` | IteracionVersion | DisenadorGrafico | RepositorioVersiones | PiezaGrafica | `E` | restaurar una versión | — |
| `OP-DIS-06` | IteracionVersion | DisenadorGrafico | RepositorioVersiones | PiezaGrafica | `L` | comparar versiones | — |
| `OP-DIS-07` | IteracionVersion | DisenadorGrafico | ComentariosAnclados | PiezaGrafica | `E` | resolver un comentario | — |
| `OP-DIS-08` | IteracionVersion | DisenadorGrafico | ComentariosAnclados | PiezaGrafica | `E` | responder un comentario | — |
| `OP-DIS-09` | ChecklistEntrega | DisenadorGrafico | ComentariosAnclados | PiezaEnRevision | `E` | corregir los ítems marcados | — |
| `OP-DIS-10` | ChecklistEntrega | DisenadorGrafico | ComentariosAnclados | PiezaEnRevision | `E` | marcar un ítem como resuelto | — |
| `OP-DIS-11` | ChecklistEntrega | DisenadorGrafico | ComentariosAnclados | PiezaEnRevision | `L` | repasar la pieza | — |
| `OP-RED-01` | CoCreacionPieza | Redactor | EditorTextoCompartido | GuionCopy | `E` | escribir el copy | — |
| `OP-RED-02` | CoCreacionPieza | Redactor | EditorTextoCompartido | GuionCopy | `E` | ajustar titulares | — |
| `OP-RED-03` | CoCreacionPieza | Redactor | EditorTextoCompartido | GuionCopy | `E` | comentar un párrafo | — |
| `OP-RED-04` | IteracionVersion | Redactor | RepositorioVersiones | GuionCopy | `E` | corregir los textos observados | — |
| `OP-RED-05` | IteracionVersion | Redactor | RepositorioVersiones | GuionCopy | `E` | versionar el copy | `TR-08` |
| `OP-MOT-01` | CoCreacionPieza | MotionDesigner | EditorGraficoColaborativo | PiezaGrafica | `E` | animar transiciones | — |
| `OP-MOT-02` | CoCreacionPieza | MotionDesigner | EditorGraficoColaborativo | PiezaGrafica | `L` | previsualizar el render | — |
| `OP-MOT-03` | CoCreacionPieza | MotionDesigner | EditorGraficoColaborativo | PaqueteExportacion | `E` | exportar el paquete | `TR-09` |
| `OP-REV-01` | CriticaColectiva | RevisorDeCalidad | ChatGeneral | RegistroCritica | `E` | registrar objeciones | `TR-03` |
| `OP-REV-02` | CriticaColectiva | RevisorDeCalidad | ChatGeneral | ChecklistCalidad | `L` | verificar estándares | — |
| `OP-REV-03` | CriticaColectiva | RevisorDeCalidad | ChatGeneral | ChecklistCalidad | `L` | citar el checklist | — |
| `OP-REV-04` | ChecklistEntrega | RevisorDeCalidad | VerificadorEntrega | ChecklistCalidad | `E` | aplicar el checklist | — |
| `OP-REV-05` | ChecklistEntrega | RevisorDeCalidad | VerificadorEntrega | ChecklistCalidad | `E` | abrir correcciones | — |
| `OP-REV-06` | ChecklistEntrega | RevisorDeCalidad | VerificadorEntrega | ChecklistCalidad | `E` | cerrar ítems | — |
| `OP-REV-07` | ChecklistEntrega | RevisorDeCalidad | ComentariosAnclados | PiezaEnRevision | `E` | señalar el punto exacto | — |
| `OP-REV-08` | ChecklistEntrega | RevisorDeCalidad | ComentariosAnclados | PiezaEnRevision | `E` | responder al diseñador | — |
| `OP-PAR-01` | CriticaColectiva | ParCreativo | PizarraAnotaciones | PiezaEnRevision | `E` | objetar la pieza | `TR-06` |
| `OP-PAR-02` | CriticaColectiva | ParCreativo | PizarraAnotaciones | PiezaEnRevision | `E` | marcar zonas | — |
| `OP-PAR-03` | CriticaColectiva | ParCreativo | PizarraAnotaciones | PiezaEnRevision | `E` | proponer ajustes concretos | — |

---

## 4. Transiciones

| ID | Tipo | Desde | Hacia | Ámbito | Disparador |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `TR-01` | handoff | CreativoSenior | DirectorDeArte | proceso | Se aprueba el rumbo |
| `TR-02` | handoff | DisenadorGrafico | RevisorDeCalidad | proceso | El Director valida la versión |
| `TR-03` | handoff | RevisorDeCalidad | DirectorDeArte | protocolo | Se cierra la crítica |
| `TR-04` | handoff | DirectorDeArte | ParCreativo | protocolo | Comienza la crítica de su propia pieza |
| `TR-05` | handoff | Cliente | EjecutivoDeCuenta | proceso | Termina la ronda de feedback |
| `TR-06` | handoff | ParCreativo | RevisorDeCalidad | protocolo | Se registra la crítica |
| `TR-07` | handoff | EjecutivoDeCuenta | DirectorDeArte | protocolo | Inicia la defensa |
| `TR-08` | handoff | Redactor | DisenadorGrafico | protocolo | Se cierra el texto |
| `TR-09` | handoff | MotionDesigner | DisenadorGrafico | protocolo | Termina el render |

Los handoffs de ámbito `proceso` se completan en [`proceso.md`](proceso.md) §3
(`PR-03`, `PR-05`, `PR-15`); los de ámbito `protocolo`, en §6. Todos los roles de este proyecto son desempeñados por
personas distintas: **no se declaran mutaciones de rol** (`Tipo = mutación`). Si un
protocolo necesitara que un mismo usuario cambie de rol dentro de una sesión, se
agregaría una fila con `Tipo = mutación` antes de dibujar.

---

## 5. Proceso

El proceso —qué dispara una transición, los 13 estados, las 15 transiciones `PR-` y sus
reglas— vive en [`proceso.md`](proceso.md). Aquí solo queda el enlace de los handoffs de
ámbito `proceso`: `TR-01`, `TR-02` y `TR-05` se materializan en `PR-03`, `PR-05` y
`PR-15`, dentro de [`proceso.md`](proceso.md) §3.

---

## 6. Protocolo

Cada actividad tiene un protocolo propio. Los estados son las operaciones habilitadas en
un momento; las transiciones `PT-` cambian de estado y declaran rol, operación,
disparador, guarda y efecto. Los handoffs de ámbito `protocolo` (`TR-03`, `TR-04`,
`TR-06`, `TR-07`, `TR-08`, `TR-09`) se marcan en la última columna.

### 6.0 Resumen

| # | Actividad | Estados | Transiciones | Handoffs de protocolo |
| :--- | :--- | :--- | :--- | :--- |
| 1 | BriefingCreativo | 5 | `PT-01`–`PT-07` | — |
| 2 | CuraduriaReferencias | 4 | `PT-08`–`PT-14` | — |
| 3 | CoCreacionPieza | 4 | `PT-15`–`PT-20` | `TR-09` |
| 4 | IteracionVersion | 4 | `PT-21`–`PT-26` | `TR-08` |
| 5 | CriticaColectiva | 4 | `PT-27`–`PT-32` | `TR-03` · `TR-04` · `TR-06` |
| 6 | ChecklistEntrega | 4 | `PT-33`–`PT-38` | — |
| 7 | PresentacionPropuesta | 4 | `PT-39`–`PT-44` | `TR-07` |
| 8 | RondaFeedback | 4 | `PT-45`–`PT-50` | — |

### 6.1 BriefingCreativo

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Apertura` | `(EjecutivoDeCuenta) VideoReunion->traducir el pedido()` (`OP-EJE-01`) · `(DirectorDeArte) PizarraColaborativa->marcar el territorio()` (`OP-DIR-01`) | BriefingCampana · DocumentoConcepto |
| `Lectura del brief` | `(Cliente) VideoReunion->validar objetivos y alcance()` (`OP-CLI-01`) · `(CreativoSenior) ChatGeneral->formular preguntas creativas()` (`OP-CRE-01`) | BriefingCampana |
| `Preguntas` | `(EjecutivoDeCuenta) VideoReunion->conducir la ronda de preguntas()` (`OP-EJE-02`) · `(Cliente) VideoReunion->responder preguntas del brief()` (`OP-CLI-02`) · `(CreativoSenior) ChatGeneral->compartir enlaces()` (`OP-CRE-03`) | BriefingCampana |
| `Acuerdos` | `(DirectorDeArte) PizarraColaborativa->anotar restricciones()` (`OP-DIR-02`) · `(EjecutivoDeCuenta) VideoReunion->cerrar acuerdos()` (`OP-EJE-03`) | DocumentoConcepto · BriefingCampana |
| `Cierre` | `(DirectorDeArte) PizarraColaborativa->confirmar el rumbo()` (`OP-DIR-03`) · `(CreativoSenior) ChatGeneral->anotar hallazgos()` (`OP-CRE-02`) | DocumentoConcepto |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-01` | `Inicio` | `Apertura` | EjecutivoDeCuenta | `VideoReunion->traducir el pedido()` (`OP-EJE-01`) | Se convoca la sesión | El brief existe y los 4 participantes están citados | Se abre la sala y se presenta el pedido | — |
| `PT-02` | `Apertura` | `Lectura del brief` | CreativoSenior | `ChatGeneral->formular preguntas creativas()` (`OP-CRE-01`) | El pedido quedó presentado | El brief está compartido en pantalla | El equipo lee el brief y formula las primeras preguntas | — |
| `PT-03` | `Lectura del brief` | `Preguntas` | EjecutivoDeCuenta | `VideoReunion->conducir la ronda de preguntas()` (`OP-EJE-02`) | Se completó la lectura | Cada participante leyó el brief | Se abre la ronda de preguntas | — |
| `PT-04` | `Preguntas` | `Lectura del brief` | CreativoSenior | `ChatGeneral->formular preguntas creativas()` (`OP-CRE-01`) | Una respuesta abre una duda de lectura | Queda una duda sin responder | Se vuelve a leer el fragmento observado | — |
| `PT-05` | `Preguntas` | `Acuerdos` | EjecutivoDeCuenta | `VideoReunion->cerrar acuerdos()` (`OP-EJE-03`) | No quedan dudas abiertas | Todas las preguntas tienen respuesta | Se fijan objetivos, alcance y restricciones | — |
| `PT-06` | `Acuerdos` | `Cierre` | DirectorDeArte | `PizarraColaborativa->anotar restricciones()` (`OP-DIR-02`) | El Cliente valida objetivos y alcance | El acta de acuerdos está completa | Se anotan las restricciones finales | — |
| `PT-07` | `Cierre` | `Fin` | DirectorDeArte | `PizarraColaborativa->confirmar el rumbo()` (`OP-DIR-03`) | El Director confirma el rumbo | BriefingCampana firmado | El brief queda como fuente para CuraduriaReferencias | — |

### 6.2 CuraduriaReferencias

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Exploración` | `(CreativoSenior) TableroReferencias->cargar referencias()` (`OP-CRE-04`) · `(CreativoSenior) TableroReferencias->comentar una referencia()` (`OP-CRE-07`) | TableroMoodboard |
| `Curación` | `(CreativoSenior) TableroReferencias->agrupar por territorio()` (`OP-CRE-05`) · `(CreativoSenior) TableroReferencias->descartar lo que no encaja()` (`OP-CRE-06`) | TableroMoodboard |
| `Territorio` | `(DirectorDeArte) TableroReferencias->elegir el territorio()` (`OP-DIR-04`) · `(DirectorDeArte) TableroReferencias->definir el criterio()` (`OP-DIR-05`) · `(DirectorDeArte) TableroReferencias->descartar referencias()` (`OP-DIR-06`) | TableroMoodboard |
| `Validación` | `(EjecutivoDeCuenta) ForoHilosCreativos->verificar el encaje con el brief()` (`OP-EJE-04`) · `(EjecutivoDeCuenta) ForoHilosCreativos->marcar faltantes()` (`OP-EJE-05`) · `(EjecutivoDeCuenta) ForoHilosCreativos->responder dudas()` (`OP-EJE-06`) | TableroMoodboard · BriefingCampana |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-08` | `Inicio` | `Exploración` | CreativoSenior | `TableroReferencias->cargar referencias()` (`OP-CRE-04`) | Se abre el tablero con el brief | El brief está cerrado | Se cargan referencias sin filtrar | — |
| `PT-09` | `Exploración` | `Curación` | CreativoSenior | `TableroReferencias->comentar una referencia()` (`OP-CRE-07`) | Hay referencias suficientes | Al menos 3 por territorio | Se comenta y agrupa el material | — |
| `PT-10` | `Curación` | `Territorio` | CreativoSenior | `TableroReferencias->agrupar por territorio()` (`OP-CRE-05`) | El material está agrupado | Cada referencia tiene territorio | El Director elige el territorio y el criterio | — |
| `PT-11` | `Territorio` | `Curación` | DirectorDeArte | `TableroReferencias->descartar referencias()` (`OP-DIR-06`) | Un territorio no alcanza el criterio | Faltan referencias para el territorio elegido | Se descartan las que no encajan y se vuelve a curar | — |
| `PT-12` | `Territorio` | `Validación` | DirectorDeArte | `TableroReferencias->elegir el territorio()` (`OP-DIR-04`) | Hay un territorio elegido | El criterio está escrito en el tablero | El Ejecutivo verifica el encaje con el brief | `TR-01` → `PR-03` |
| `PT-13` | `Validación` | `Curación` | EjecutivoDeCuenta | `ForoHilosCreativos->marcar faltantes()` (`OP-EJE-05`) | El brief no está cubierto | Algún objetivo del brief queda sin referencia | Se marcan faltantes y se vuelve a curar | — |
| `PT-14` | `Validación` | `Fin` | EjecutivoDeCuenta | `ForoHilosCreativos->verificar el encaje con el brief()` (`OP-EJE-04`) | El encaje con el brief se verifica | El brief queda cubierto | Se habilita `PR-03` (`TR-01`) | — |

### 6.3 CoCreacionPieza

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Encuadre` | `(DirectorDeArte) CanalVozEquipo->marcar el encuadre()` (`OP-DIR-07`) | PiezaGrafica |
| `Composición` | `(DisenadorGrafico) EditorGraficoColaborativo->componer la pieza base()` (`OP-DIS-01`) · `(DisenadorGrafico) EditorGraficoColaborativo->bloquear una capa()` (`OP-DIS-03`) · `(Redactor) EditorTextoCompartido->escribir el copy()` (`OP-RED-01`) · `(Redactor) EditorTextoCompartido->ajustar titulares()` (`OP-RED-02`) | PiezaGrafica · GuionCopy |
| `Integración` | `(DisenadorGrafico) EditorGraficoColaborativo->integrar capas y estilos()` (`OP-DIS-02`) · `(MotionDesigner) EditorGraficoColaborativo->animar transiciones()` (`OP-MOT-01`) · `(MotionDesigner) EditorGraficoColaborativo->previsualizar el render()` (`OP-MOT-02`) · `(Redactor) EditorTextoCompartido->comentar un párrafo()` (`OP-RED-03`) | PiezaGrafica · GuionCopy |
| `Revisión rápida` | `(DirectorDeArte) CanalVozEquipo->aprobar la dirección visual()` (`OP-DIR-08`) · `(DirectorDeArte) CanalVozEquipo->pedir ajustes en vivo()` (`OP-DIR-09`) · `(MotionDesigner) EditorGraficoColaborativo->exportar el paquete()` (`OP-MOT-03`) | PiezaGrafica · PaqueteExportacion |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-15` | `Inicio` | `Encuadre` | DirectorDeArte | `CanalVozEquipo->marcar el encuadre()` (`OP-DIR-07`) | Se abre el lienzo | El rumbo aprobado está disponible | El Director marca el encuadre | — |
| `PT-16` | `Encuadre` | `Composición` | DisenadorGrafico | `EditorGraficoColaborativo->componer la pieza base()` (`OP-DIS-01`) | El encuadre está marcado | El Director aprobó el encuadre | Se compone la pieza base y arranca el copy | — |
| `PT-17` | `Composición` | `Integración` | Redactor | `EditorTextoCompartido->ajustar titulares()` (`OP-RED-02`) | El texto está cerrado | Titulares y copy aprobados por el Director | El Diseñador recibe el texto para integrarlo | — |
| `PT-18` | `Integración` | `Revisión rápida` | MotionDesigner | `EditorGraficoColaborativo->previsualizar el render()` (`OP-MOT-02`) | El render está listo | Capas, copy y motion integrados | El Diseñador recibe el render para la revisión | — |
| `PT-19` | `Revisión rápida` | `Integración` | DirectorDeArte | `CanalVozEquipo->pedir ajustes en vivo()` (`OP-DIR-09`) | La dirección visual no se aprueba | Hay ajustes concretos | Se vuelve a integrar con los ajustes | — |
| `PT-20` | `Revisión rápida` | `Fin` | MotionDesigner | `EditorGraficoColaborativo->exportar el paquete()` (`OP-MOT-03`) | La dirección visual se aprueba | Paquete exportado sin errores | El Diseñador recibe el paquete; la pieza queda lista para `PR-04` | `TR-09` |

### 6.4 IteracionVersion

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Comentarios` | `(DirectorDeArte) ComentariosAnclados->priorizar correcciones()` (`OP-DIR-10`) · `(DirectorDeArte) ComentariosAnclados->reabrir un ítem()` (`OP-DIR-12`) | PiezaGrafica |
| `Ajustes` | `(DisenadorGrafico) ComentariosAnclados->resolver un comentario()` (`OP-DIS-07`) · `(DisenadorGrafico) ComentariosAnclados->responder un comentario()` (`OP-DIS-08`) · `(Redactor) RepositorioVersiones->corregir los textos observados()` (`OP-RED-04`) | PiezaGrafica · GuionCopy |
| `Nueva versión` | `(DisenadorGrafico) RepositorioVersiones->publicar una nueva versión()` (`OP-DIS-04`) · `(DisenadorGrafico) RepositorioVersiones->restaurar una versión()` (`OP-DIS-05`) · `(Redactor) RepositorioVersiones->versionar el copy()` (`OP-RED-05`) | PiezaGrafica · GuionCopy |
| `Validación` | `(DisenadorGrafico) RepositorioVersiones->comparar versiones()` (`OP-DIS-06`) · `(DirectorDeArte) ComentariosAnclados->dar el visto bueno()` (`OP-DIR-11`) | PiezaGrafica |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-21` | `Inicio` | `Comentarios` | DirectorDeArte | `ComentariosAnclados->priorizar correcciones()` (`OP-DIR-10`) | Hay una versión publicada | La versión tiene comentarios abiertos | El Director prioriza las correcciones | — |
| `PT-22` | `Comentarios` | `Ajustes` | DisenadorGrafico | `ComentariosAnclados->resolver un comentario()` (`OP-DIS-07`) | Las correcciones están priorizadas | Cada comentario tiene responsable | Se resuelven los comentarios y se corrige el copy | — |
| `PT-23` | `Ajustes` | `Nueva versión` | Redactor | `RepositorioVersiones->versionar el copy()` (`OP-RED-05`) | Los ajustes están completos | Textos y pieza corregidos | El Diseñador recibe el copy versionado para publicar | `TR-08` |
| `PT-24` | `Nueva versión` | `Validación` | DisenadorGrafico | `RepositorioVersiones->publicar una nueva versión()` (`OP-DIS-04`) | La versión está lista | La pieza exporta sin errores | Se publica la versión y se compara con la anterior | — |
| `PT-25` | `Validación` | `Comentarios` | DirectorDeArte | `ComentariosAnclados->reabrir un ítem()` (`OP-DIR-12`) | El visto bueno no se otorga | Queda un ítem abierto | Se reabre el ítem y vuelve a comentarios | — |
| `PT-26` | `Validación` | `Fin` | DirectorDeArte | `ComentariosAnclados->dar el visto bueno()` (`OP-DIR-11`) | No quedan ítems abiertos | El Director dio el visto bueno | La versión validada queda lista para `PR-05` (`TR-02`) | — |

### 6.5 CriticaColectiva

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Presentación` | `(DirectorDeArte) VideoReunion->moderar la crítica()` (`OP-DIR-13`) · `(DirectorDeArte) VideoReunion->ceder la palabra()` (`OP-DIR-14`) | RegistroCritica |
| `Objeciones` | `(ParCreativo) PizarraAnotaciones->objetar la pieza()` (`OP-PAR-01`) · `(ParCreativo) PizarraAnotaciones->marcar zonas()` (`OP-PAR-02`) · `(ParCreativo) PizarraAnotaciones->proponer ajustes concretos()` (`OP-PAR-03`) | PiezaEnRevision |
| `Registro` | `(RevisorDeCalidad) ChatGeneral->registrar objeciones()` (`OP-REV-01`) · `(RevisorDeCalidad) ChatGeneral->verificar estándares()` (`OP-REV-02`) · `(RevisorDeCalidad) ChatGeneral->citar el checklist()` (`OP-REV-03`) | RegistroCritica · ChecklistCalidad |
| `Veredicto` | `(DirectorDeArte) VideoReunion->emitir el veredicto()` (`OP-DIR-15`) | RegistroCritica |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-27` | `Inicio` | `Presentación` | DirectorDeArte | `VideoReunion->moderar la crítica()` (`OP-DIR-13`) | Se abre la sesión con la pieza congelada | La pieza está publicada y sin cambios | El Director modera y presenta la pieza | — |
| `PT-28` | `Presentación` | `Objeciones` | ParCreativo | `PizarraAnotaciones->objetar la pieza()` (`OP-PAR-01`) | El Director cede la palabra | El Par no produjo la pieza | El ParCreativo objeta la pieza | `TR-04` |
| `PT-29` | `Objeciones` | `Registro` | RevisorDeCalidad | `ChatGeneral->registrar objeciones()` (`OP-REV-01`) | Hay objeciones sobre la mesa | Cada objeción tiene zona y propuesta | El Revisor registra las objeciones | `TR-06` |
| `PT-30` | `Registro` | `Veredicto` | DirectorDeArte | `VideoReunion->emitir el veredicto()` (`OP-DIR-15`) | Las objeciones están registradas | No quedan objeciones sin registrar | El Director emite el veredicto | `TR-03` |
| `PT-31` | `Veredicto` | `Objeciones` | ParCreativo | `PizarraAnotaciones->proponer ajustes concretos()` (`OP-PAR-03`) | El veredicto pide una objeción más | Falta una zona por revisar | Se propone un ajuste concreto y se vuelve a objeciones | — |
| `PT-32` | `Veredicto` | `Fin` | DirectorDeArte | `VideoReunion->emitir el veredicto()` (`OP-DIR-15`) | El veredicto está completo | Todas las objeciones están registradas | Pasa a ChecklistEntrega o vuelve a IteracionVersion | — |

### 6.6 ChecklistEntrega

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Checklist` | `(RevisorDeCalidad) VerificadorEntrega->aplicar el checklist()` (`OP-REV-04`) · `(RevisorDeCalidad) VerificadorEntrega->abrir correcciones()` (`OP-REV-05`) | ChecklistCalidad |
| `Correcciones` | `(DisenadorGrafico) ComentariosAnclados->corregir los ítems marcados()` (`OP-DIS-09`) · `(DisenadorGrafico) ComentariosAnclados->marcar un ítem como resuelto()` (`OP-DIS-10`) · `(RevisorDeCalidad) ComentariosAnclados->señalar el punto exacto()` (`OP-REV-07`) | PiezaEnRevision |
| `Repaso` | `(DisenadorGrafico) ComentariosAnclados->repasar la pieza()` (`OP-DIS-11`) · `(RevisorDeCalidad) ComentariosAnclados->responder al diseñador()` (`OP-REV-08`) · `(RevisorDeCalidad) VerificadorEntrega->cerrar ítems()` (`OP-REV-06`) | PiezaEnRevision · ChecklistCalidad |
| `Aprobación` | `(DirectorDeArte) VerificadorEntrega->aprobar la entrega()` (`OP-DIR-16`) · `(DirectorDeArte) VerificadorEntrega->firmar el pase()` (`OP-DIR-17`) | ChecklistCalidad |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-33` | `Inicio` | `Checklist` | RevisorDeCalidad | `VerificadorEntrega->aplicar el checklist()` (`OP-REV-04`) | Se abre el checklist | La pieza pasó la crítica | El Revisor aplica el estándar | — |
| `PT-34` | `Checklist` | `Correcciones` | RevisorDeCalidad | `VerificadorEntrega->abrir correcciones()` (`OP-REV-05`) | Hay ítems no conformes | Al menos un ítem falla | Se abren correcciones con punto exacto | — |
| `PT-35` | `Correcciones` | `Repaso` | DisenadorGrafico | `ComentariosAnclados->marcar un ítem como resuelto()` (`OP-DIS-10`) | Los ítems están corregidos | Cada ítem tiene marca de resuelto | El Diseñador repasa la pieza | — |
| `PT-36` | `Repaso` | `Checklist` | RevisorDeCalidad | `ComentariosAnclados->responder al diseñador()` (`OP-REV-08`) | Un ítem vuelve a fallar | El repaso detecta una regresión | Se reabre el checklist | — |
| `PT-37` | `Repaso` | `Aprobación` | RevisorDeCalidad | `VerificadorEntrega->cerrar ítems()` (`OP-REV-06`) | El checklist está completo | 100% de ítems cerrados | El Director aprueba y firma | — |
| `PT-38` | `Aprobación` | `Fin` | DirectorDeArte | `VerificadorEntrega->firmar el pase()` (`OP-DIR-17`) | El Director firma el pase | Checklist firmado por Revisor y Director | Se habilita `PR-11` | — |

### 6.7 PresentacionPropuesta

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Apertura` | `(EjecutivoDeCuenta) VideoReunion->conducir la presentación()` (`OP-EJE-07`) | PropuestaComercial |
| `Recorrido` | `(DirectorDeArte) PresentadorSlides->defender la propuesta()` (`OP-DIR-18`) · `(DirectorDeArte) PresentadorSlides->ajustar el relato en vivo()` (`OP-DIR-19`) | PropuestaComercial |
| `Objeciones` | `(Cliente) VideoReunion->plantear objeciones()` (`OP-CLI-03`) · `(EjecutivoDeCuenta) VideoReunion->registrar objeciones()` (`OP-EJE-08`) | PropuestaComercial |
| `Acuerdo` | `(Cliente) VideoReunion->manifestar acuerdo()` (`OP-CLI-04`) · `(EjecutivoDeCuenta) VideoReunion->cerrar el acuerdo()` (`OP-EJE-09`) | PropuestaComercial |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-39` | `Inicio` | `Apertura` | EjecutivoDeCuenta | `VideoReunion->conducir la presentación()` (`OP-EJE-07`) | Se abre la presentación | La pieza está aprobada y la propuesta cargada | El Ejecutivo conduce la apertura | — |
| `PT-40` | `Apertura` | `Recorrido` | DirectorDeArte | `PresentadorSlides->defender la propuesta()` (`OP-DIR-18`) | El Cliente está en la sala | El Ejecutivo cedió la palabra | El Director defiende la propuesta | `TR-07` |
| `PT-41` | `Recorrido` | `Objeciones` | Cliente | `VideoReunion->plantear objeciones()` (`OP-CLI-03`) | Termina el recorrido | El Director terminó la defensa | El Cliente plantea objeciones | — |
| `PT-42` | `Objeciones` | `Recorrido` | DirectorDeArte | `PresentadorSlides->ajustar el relato en vivo()` (`OP-DIR-19`) | Una objeción pide más contexto | La objeción no está resuelta | Se ajusta el relato y se vuelve al recorrido | — |
| `PT-43` | `Objeciones` | `Acuerdo` | EjecutivoDeCuenta | `VideoReunion->registrar objeciones()` (`OP-EJE-08`) | Todas las objeciones están registradas | Cada objeción tiene respuesta | Se busca el acuerdo | — |
| `PT-44` | `Acuerdo` | `Fin` | EjecutivoDeCuenta | `VideoReunion->cerrar el acuerdo()` (`OP-EJE-09`) | El Cliente manifiesta acuerdo | El acta de la reunión está completa | Se habilita `PR-12` | — |

### 6.8 RondaFeedback

**Estados y operaciones habilitadas**

| Estado | Operaciones habilitadas | Artefacto |
| :--- | :--- | :--- |
| `Publicación` | `(EjecutivoDeCuenta) ComentariosPorHilo->ordenar el feedback()` (`OP-EJE-10`) | HiloFeedback |
| `Lectura` | `(Cliente) PortalCliente->descargar la propuesta()` (`OP-CLI-07`) · `(Cliente) PortalCliente->comentar la pieza()` (`OP-CLI-05`) | HiloFeedback |
| `Comentarios` | `(EjecutivoDeCuenta) ComentariosPorHilo->derivar correcciones()` (`OP-EJE-11`) · `(DirectorDeArte) ComentariosPorHilo->aceptar o rechazar un comentario()` (`OP-DIR-20`) · `(DirectorDeArte) ComentariosPorHilo->responder objeciones()` (`OP-DIR-21`) | HiloFeedback |
| `Cierre` | `(Cliente) PortalCliente->marcar aprobaciones()` (`OP-CLI-06`) · `(EjecutivoDeCuenta) ComentariosPorHilo->confirmar el cierre()` (`OP-EJE-12`) | ActaAprobacion · HiloFeedback |

**Transiciones**

| ID | Desde | Hacia | Rol | Operación (herramienta) | Disparador | Guarda | Efecto | Transición |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PT-45` | `Inicio` | `Publicación` | EjecutivoDeCuenta | `ComentariosPorHilo->ordenar el feedback()` (`OP-EJE-10`) | Se abre la ronda | La presentación terminó y la pieza está publicada | El Ejecutivo ordena el feedback y habilita el portal | — |
| `PT-46` | `Publicación` | `Lectura` | Cliente | `PortalCliente->descargar la propuesta()` (`OP-CLI-07`) | El Cliente recibe acceso | El portal muestra la pieza presentada | El Cliente descarga la propuesta y lee la pieza | — |
| `PT-47` | `Lectura` | `Comentarios` | Cliente | `PortalCliente->comentar la pieza()` (`OP-CLI-05`) | El Cliente terminó la lectura | La pieza fue vista completa | El Cliente comenta por hilo | — |
| `PT-48` | `Comentarios` | `Lectura` | Cliente | `PortalCliente->descargar la propuesta()` (`OP-CLI-07`) | Falta contexto sobre la pieza | El comentario no se puede fundamentar | Se vuelve a leer la propuesta | — |
| `PT-49` | `Comentarios` | `Cierre` | EjecutivoDeCuenta | `ComentariosPorHilo->derivar correcciones()` (`OP-EJE-11`) | No quedan hilos abiertos | Cada comentario está clasificado | Se derivan correcciones y se pide la decisión | — |
| `PT-50` | `Cierre` | `Fin` | Cliente | `PortalCliente->marcar aprobaciones()` (`OP-CLI-06`) | El Cliente marca aprobaciones | ActaAprobacion firmada | Se habilita `PR-15` (`TR-05`); si pide cambios, `PR-14` | `TR-05` → `PR-15` |

### 6.9 Reglas del protocolo

- **Un estado es una operación habilitada.** El estado no describe una intención: enumera las operaciones que el rol puede ejecutar en ese momento.
- **Toda `PT-` referencia una `OP-`.** Si una transición necesita una operación que no está en §3, se detiene el protocolo y se corrige la matriz.
- **Los handoffs de protocolo son seis.** `TR-03`, `TR-04`, `TR-06`, `TR-07`, `TR-08` y `TR-09` cambian el rol activo dentro de una actividad; no hay mutaciones de rol.
- **Los retornos no reinician el protocolo.** Vuelven al estado anterior con una guarda concreta y un alcance acotado.

---

## 7. Validación

| # | Regla | Verificación en Oficina | Estado |
| :--- | :--- | :--- | :--- |
| C1 | Cobertura rol↔actividad | 9 roles en el catálogo; los 9 aparecen en §2 y en §3. | ✅ |
| C2 | Regla de oro | Las 8 actividades tienen al menos un canal: VideoReunion, ForoHilosCreativos, CanalVozEquipo, ComentariosAnclados, ChatGeneral, ComentariosPorHilo o PortalCliente. | ✅ |
| C3 | Operación completa | 77 filas, 77 operaciones atómicas; todas con actividad, herramienta, artefacto y modo. | ✅ |
| C4 | Sin huérfanos | Las 15 herramientas únicas y los 12 artefactos declarados se usan al menos una vez. | ✅ |
| C5 | Temporalidad | Las 4 actividades sincrónicas usan solo herramientas sincrónicas; las 4 asincrónicas, solo asincrónicas. | ✅ |
| C6 | Visibilidad | El Cliente solo lee `BriefingCampana` y `PropuestaComercial`, y escribe `HiloFeedback` y `ActaAprobacion`; no toca `PiezaGrafica` ni `PiezaEnRevision`. | ✅ |
| C7 | Segregación de funciones | El Disenador publica y hace handoff al Revisor (`TR-02`); el Director aprueba la entrega; el Par critica la pieza del Director (`TR-04`). | ✅ |
| C8 | Multiplicidad | Todos los roles tienen multiplicidad `1`; el proyecto no usa quórum. | ✅ |
| C9 | Nombres e IDs | 77 `OP-`, 9 `TR-`, 15 `PR-` (en `proceso.md`) y 50 `PT-`, todos únicos y con nombres que coinciden con las fichas. | ✅ |
| C10 | Fuente única | `oficina.md` §3 indexa roles por workspace y enlaza aquí; §4 declara el awareness y referencia `proceso.md` y §6 para proceso y protocolo. | ✅ |
| C11 | Proceso completo | `proceso.md` declara 8 actividades, 3 decisiones, `Inicio` y `Fin`; 15 `PR-` con rol, acción, herramienta, artefacto, disparador, guarda y efecto. | ✅ |
| C12 | Handoffs de proceso | `proceso.md` §3 materializa `TR-01`, `TR-02` y `TR-05` en `PR-03`, `PR-05` y `PR-15`. | ✅ |
| C13 | Protocolo completo | 8 protocolos, 33 estados y 50 `PT-`; cada `PT-` tiene rol, operación, disparador, guarda y efecto. | ✅ |
| C14 | Handoffs de protocolo | `TR-03`, `TR-04`, `TR-06`, `TR-07`, `TR-08` y `TR-09` se materializan en `PT-30`, `PT-28`, `PT-29`, `PT-40`, `PT-23` y `PT-20`. | ✅ |
| C15 | Trazabilidad | Toda `PT-` referencia una `OP-` de §3; cada `TR-` tiene exactamente una operación en `Dispara`. | ✅ |

---

## 8. Estado

- **Pasos 1–7 completos.** Workspaces, sesiones, roles, operaciones, transiciones, awareness, proceso y protocolo están declarados y validados.
- **Archivos por capa.** [`roles.md`](roles.md) para roles, operaciones, handoffs y protocolos; [`proceso.md`](proceso.md) para el proceso.
- **Diagramas.** [`diagramas/03-proceso.drawio`](diagramas/03-proceso.drawio) y [`diagramas/04-protocolos.drawio`](diagramas/04-protocolos.drawio).
- **Mutaciones.** No se declaran: todos los roles son personas distintas.
- **Fuera de Oficina.** El proyecto educativo sigue en el paso 3; su `roles.md` es el siguiente trabajo.
