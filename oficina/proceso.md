# Proceso colaborativo — Oficina

**CSSL · Fase inter-actividad: proceso**

> Fuente única del proceso de la agencia. El diagrama está en
> [`diagramas/03-proceso.drawio`](diagramas/03-proceso.drawio). Los roles y las
> operaciones viven en [`roles.md`](roles.md); los protocolos por actividad, en
> [`roles.md`](roles.md) §6.

---

## 1. Qué dispara una transición

Una transición `PR-` no se produce por el paso del tiempo ni por un cambio automático
del sistema: se produce cuando **un rol ejecuta una operación** de la matriz
([`roles.md`](roles.md) §3). Esa operación es el hecho observable que mueve al grupo de
un estado a otro.

En la práctica, la operación que dispara la transición suele responder a uno de dos
motivos:

1. **Cerrar la actividad anterior.** El rol responsable ejecuta la operación que deja la
   actividad en su criterio de salida —publicar la versión, firmar el pase, emitir el
   veredicto—. El grupo pasa a la siguiente actividad.
2. **Pasar a evaluar una situación.** Un rol abre un punto de decisión y su operación
   deja registro del veredicto: «pasa» o «vuelve», «aprobada» o «corregir», «aprobado» o
   «cambios». Según el resultado, el flujo avanza o retorna.

De ahí que cada `PR-` declare siempre **rol que actúa** y **acción de proceso** (la
operación concreta), además del disparador, la guarda y el efecto.

### 1.1 Cómo se lee una fila

| Columna | Qué responde |
| :--- | :--- |
| `ID` | Identificador de la transición (`PR-01`…`PR-15`). No es una operación: es el cambio de estado. |
| `Desde` / `Hacia` | Estados de origen y destino (`Inicio`, `E1`…`E8`, `D1`…`D3`, `Fin`). |
| `Tipo` | `apertura`, `avance`, `cierre de actividad`, `retorno` o `cierre`. |
| `Rol que actúa` | Quién ejecuta la operación que dispara el cambio. |
| `Acción de proceso` | Operación atómica (`OP-`) de [`roles.md`](roles.md) §3 que se ejecuta. |
| `Herramienta · Artefacto` | Dónde se ejecuta y sobre qué objeto queda el rastro. |
| `Disparador` | Hecho que inicia la transición. |
| `Guarda` | Condición verificable que debe cumplirse para completarla. |
| `Efecto` | Qué queda habilitado o registrado en el estado de destino. |
| `TR` | Handoff de rol que ocurre dentro de la transición, si existe. |

### 1.2 Reglas de lectura

- **El rol que actúa es el que ejecuta la `OP-`,** no necesariamente el dueño de la
  actividad de destino. `PR-04` la ejecuta MotionDesigner y abre `IteracionVersion`.
- **Disparador y guarda son cosas distintas.** El disparador inicia la transición («el
  Cliente aprueba»); la guarda es la condición que la completa («ActaAprobacion firmada»).
  Si la guarda no se cumple, el grupo permanece en el estado actual.
- **Toda `PR-` referencia una operación existente.** Si el proceso necesita una operación
  que no está en la matriz, se corrige [`roles.md`](roles.md) §3 antes de dibujar; no se
  inventa en el proceso.
- **Los handoffs no son transiciones aparte.** `TR-01`, `TR-02` y `TR-05` cambian el rol
  responsable dentro de una `PR-` y se marcan en la última columna.

---

## 2. Estados del proceso

Trece estados: dos extremos (`Inicio`, `Fin`), ocho actividades y tres decisiones.

| Estado | Tipo | Actividad / pregunta | Workspace | Rol que lo abre | Criterio de salida |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `Inicio` | inicio | — | — | EjecutivoDeCuenta | El pedido existe y el brief está citado |
| `E1` | actividad | BriefingCreativo | DireccionCreativa | EjecutivoDeCuenta | BriefingCampana validado por Cliente y DirectorDeArte |
| `E2` | actividad | CuraduriaReferencias | DireccionCreativa | CreativoSenior | Territorio elegido y encaje verificado |
| `E3` | actividad | CoCreacionPieza | EstudioProduccion | DisenadorGrafico | Pieza base y paquete exportado |
| `E4` | actividad | IteracionVersion | EstudioProduccion | DisenadorGrafico | Versión validada por el DirectorDeArte |
| `E5` | actividad | CriticaColectiva | SalaRevision | DirectorDeArte | Veredicto registrado |
| `D1` | decisión | ¿La crítica pide cambios? | SalaRevision | DirectorDeArte | Veredicto «pasa» o «vuelve» |
| `E6` | actividad | ChecklistEntrega | SalaRevision | RevisorDeCalidad | Checklist firmado |
| `D2` | decisión | ¿Checklist aprobado? | SalaRevision | DirectorDeArte | Pase firmado o correcciones abiertas |
| `E7` | actividad | PresentacionPropuesta | RelacionClientes | EjecutivoDeCuenta | Acta de la presentación cerrada |
| `E8` | actividad | RondaFeedback | RelacionClientes | EjecutivoDeCuenta | El Cliente aprobó o pidió cambios |
| `D3` | decisión | ¿Cliente aprueba? | RelacionClientes | Cliente | ActaAprobacion firmada o correcciones derivadas |
| `Fin` | fin | — | — | EjecutivoDeCuenta | Pedido cerrado y archivado |

---

## 3. Transiciones y acciones de proceso

| ID | Desde | Hacia | Tipo | Rol que actúa | Acción de proceso | Herramienta · Artefacto | Disparador | Guarda | Efecto | TR |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `PR-01` | `Inicio` | `E1` | apertura | EjecutivoDeCuenta | traducir el pedido (`OP-EJE-01`) | VideoReunion · BriefingCampana | El Cliente entrega el pedido | Existe un brief con objetivos y alcance | Se abre BriefingCreativo con los 4 participantes | — |
| `PR-02` | `E1` | `E2` | avance | CreativoSenior | cargar referencias (`OP-CRE-04`) | TableroReferencias · TableroMoodboard | Se cierra el brief | BriefingCampana validado por Cliente y DirectorDeArte | La curación arranca con el brief como criterio | — |
| `PR-03` | `E2` | `E3` | avance | DirectorDeArte | elegir el territorio (`OP-DIR-04`) | TableroReferencias · TableroMoodboard | El Director elige el territorio | ≥3 referencias por territorio y encaje verificado | El tablero se bloquea y producción recibe el rumbo | `TR-01` |
| `PR-04` | `E3` | `E4` | avance | MotionDesigner | exportar el paquete (`OP-MOT-03`) | EditorGraficoColaborativo · PaqueteExportacion | Se aprueba la dirección visual | Paquete exportado sin errores | La pieza exportada entra a IteracionVersion como versión 1 | — |
| `PR-05` | `E4` | `E5` | avance | DirectorDeArte | dar el visto bueno (`OP-DIR-11`) | ComentariosAnclados · PiezaGrafica | El Director da el visto bueno | No quedan ítems abiertos en la versión | La versión validada se congela para la crítica | `TR-02` |
| `PR-06` | `E5` | `D1` | cierre de actividad | DirectorDeArte | emitir el veredicto (`OP-DIR-15`) | VideoReunion · RegistroCritica | Se registran las objeciones | Todas las objeciones están registradas | Veredicto «pasa» o «vuelve» | — |
| `PR-07` | `D1` | `E4` | retorno | DirectorDeArte | reabrir un ítem (`OP-DIR-12`) | ComentariosAnclados · PiezaGrafica | Veredicto «vuelve» | Cada objeción tiene punto y responsable | Se reabre IteracionVersion con la lista de cambios | — |
| `PR-08` | `D1` | `E6` | avance | RevisorDeCalidad | aplicar el checklist (`OP-REV-04`) | VerificadorEntrega · ChecklistCalidad | Veredicto «pasa» | No quedan objeciones abiertas | Se habilita la verificación formal | — |
| `PR-09` | `E6` | `D2` | cierre de actividad | DirectorDeArte | firmar el pase (`OP-DIR-17`) | VerificadorEntrega · ChecklistCalidad | El Revisor cierra el checklist | Checklist 100% cerrado por el Revisor | Veredicto «aprobada» o «corregir» | — |
| `PR-10` | `D2` | `E4` | retorno | DisenadorGrafico | corregir los ítems marcados (`OP-DIS-09`) | ComentariosAnclados · PiezaEnRevision | Checklist incompleto | Cada ítem fallido tiene comentario anclado | Nueva iteración acotada a los ítems | — |
| `PR-11` | `D2` | `E7` | avance | EjecutivoDeCuenta | conducir la presentación (`OP-EJE-07`) | VideoReunion · PropuestaComercial | El Director firma el pase | Paquete exportado y propuesta actualizada | El Cliente ve solo lo presentado | — |
| `PR-12` | `E7` | `E8` | avance | EjecutivoDeCuenta | ordenar el feedback (`OP-EJE-10`) | ComentariosPorHilo · HiloFeedback | Termina la presentación | El Cliente tiene acceso al portal y el acta está cargada | Se inicia la ronda asincrónica | — |
| `PR-13` | `E8` | `D3` | cierre de actividad | EjecutivoDeCuenta | confirmar el cierre (`OP-EJE-12`) | ComentariosPorHilo · HiloFeedback | El Cliente comenta o aprueba | Todos los hilos tienen respuesta y hay decisión | Veredicto «aprobado» o «cambios» | — |
| `PR-14` | `D3` | `E4` | retorno | EjecutivoDeCuenta | derivar correcciones (`OP-EJE-11`) | ComentariosPorHilo · HiloFeedback | El Cliente pide cambios | Cada comentario está clasificado y priorizado | Vuelve a IteracionVersion | — |
| `PR-15` | `D3` | `Fin` | cierre | Cliente | marcar aprobaciones (`OP-CLI-06`) | PortalCliente · ActaAprobacion | El Cliente aprueba | ActaAprobacion firmada y pieza final entregada | El pedido se cierra y se archiva | `TR-05` |

---

## 4. Reglas del proceso

- **Sin operación no hay transición.** Cada `PR-` nombra la operación de un rol que la
  dispara; no existen avances automáticos ni temporales.
- **Sin guarda no hay avance.** Toda `PR-` tiene una condición verificable; si no se
  cumple, el grupo permanece en el estado actual.
- **Los retornos acotan el alcance.** `PR-07`, `PR-10` y `PR-14` reabren `E4` con la lista
  de cambios que motivó el retorno; no reinician el pedido.
- **Tres handoffs, no más.** Solo `TR-01`, `TR-02` y `TR-05` cambian el rol responsable
  entre actividades. Los demás `PR-` mueven al grupo sin transferir responsabilidad.
- **Nada fuera de la matriz.** Toda operación de proceso referencia una `OP-` de
  [`roles.md`](roles.md) §3. Si un `PR-` necesita una operación inexistente, se detiene el
  proceso y se corrige la matriz.
- **Las decisiones no ejecutan operaciones.** `D1`, `D2` y `D3` son compuertas: la
  operación la ejecuta el rol que las abre o el que toma la salida, y queda registrada en
  la `PR-` correspondiente.

---

## 5. Diagrama y trazabilidad

[`diagramas/03-proceso.drawio`](diagramas/03-proceso.drawio) tiene dos páginas. La primera,
«Proceso colaborativo» (1600×900), dibuja el flujo: actividades en verde, decisiones en
rombo, inicio y fin, las 15 transiciones `PR-` y los retornos en línea punteada. La
segunda, «Referencia PR» (1600×900), es la tabla de referencia de las 15 etiquetas: `PR` ·
etiqueta del arco · tramo · rol → objeto — operación, con el `OP-` que la respalda.

La primera página incluye al pie el panel «Awareness · Proceso» con `UserHistory`,
`Expectations` y `ActivityLevel`, declarados en [`oficina.md`](oficina.md) §4.

> La tabla de referencia se deriva de §3 y de [`roles.md`](roles.md) §3; si cambia una
> transición, se corrige la fuente y se actualiza la página. No introduce datos nuevos.

| Verificación | Resultado |
| :--- | :--- |
| Estados | 13: `Inicio`, 8 actividades, 3 decisiones y `Fin`. |
| Transiciones | 15 `PR-`, todas con rol, operación, herramienta, artefacto, disparador, guarda y efecto. |
| Alcanzabilidad | Las 8 actividades son alcanzables desde `Inicio`; `Fin` solo se alcanza con la guarda de `PR-15`. |
| Retornos | `PR-07`, `PR-10` y `PR-14` vuelven a `E4` y conservan la lista de cambios. |
| Handoffs de proceso | `TR-01` → `PR-03`, `TR-02` → `PR-05`, `TR-05` → `PR-15`. |
| Trazabilidad | Las 15 acciones referencian una `OP-` existente de [`roles.md`](roles.md) §3. |

La validación completa del proyecto —incluidos roles, operaciones y protocolos— está en
[`roles.md`](roles.md) §7.
