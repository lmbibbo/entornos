# Roles y Operaciones · `<Proyecto>`

**Paso 4 del algoritmo** (`agents.md` §4). Este archivo es la **fuente única** de roles,
asignación por actividad, operaciones y esqueleto de transiciones del proyecto. Las
fichas de workspace resumen los roles y enlazan aquí; no duplican la matriz.

Regla que ordena todo el documento: **un rol modifica un artefacto únicamente a través
de una herramienta declarada**. Si una operación no tiene actividad, herramienta,
artefacto y modo, no existe.

> Ejemplo completo y conforme: [`oficina/roles.md`](oficina/roles.md).

---

## Convenciones

| Elemento | Convención |
| :--- | :--- |
| **Rol** | PascalCase en singular (`DirectorDeArte`). |
| **Actividad** | PascalCase, igual que en la ficha del workspace (`BriefingCreativo`). |
| **Herramienta** | PascalCase, exactamente como se declaró en la ficha (`EditorGraficoColaborativo`). |
| **Artefacto** | PascalCase, exactamente como se declaró en la ficha (`PiezaGrafica`). |
| **Modo** | `L` = lectura · `E` = escritura. Si la operación lee y escribe el mismo artefacto, se separa en dos filas o se usa `L/E`. |
| **ID de operación** | `OP-<ROL>-<NN>` (`OP-DIR-01`). Único y estable. |
| **ID de transición** | `TR-<NN>` (`TR-01`). Único y estable. |
| **Una fila, una operación** | Cada fila de §3 contiene una sola operación atómica. |
| **Una fila, un artefacto** | Si una operación toca dos artefactos con modos distintos, se parte en dos filas. |
| **Operación atómica** | Verbo en infinitivo + objeto observable (`publicar una nueva versión`). No mezclar dos acciones incompatibles. |

---

## 1. Catálogo de roles

| Rol | Propósito | Tipo | Workspaces |
| :--- | :--- | :--- | :--- |
| `<Rol>` | Qué decide, produce o garantiza. | interno / externo | `<Workspace1>` · `<Workspace2>` |
| `<RolApoyo>` | Qué aporta al proceso sin producir la pieza. | interno | `<Workspace1>` |

**Reglas de esta sección**

- Todo rol que aparezca en una actividad debe estar en esta tabla.
- Todo rol de esta tabla debe aparecer en al menos una actividad de §2.
- Un rol `externo` no puede escribir en artefactos internos; su visibilidad se valida en §5.

---

## 2. Asignación rol-actividad

| Actividad | Workspace | Tipo | Rol | Multiplicidad | Herramienta(s) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `<Actividad>` | `<Workspace>` | sincrónica | `<Rol>` | `1` | `<HerramientaComunicacion>` |
| `<Actividad>` | `<Workspace>` | sincrónica | `<RolApoyo>` | `1..N` | `<HerramientaProduccion>` |

**Reglas de esta sección**

- La multiplicidad expresa cuántos usuarios pueden ejercer el rol en esa actividad: `1`, `0..1`, `1..N`.
- Una fila por rol y herramienta. Si el rol usa dos herramientas en la actividad, se declaran dos filas.
- La modalidad de la actividad y la de sus herramientas debe coincidir (paso 3).
- Toda actividad necesita al menos un rol y al menos una herramienta de comunicación.

---

## 3. Matriz de operaciones

| ID | Actividad | Rol | Herramienta | Artefacto | Modo | Operación | Dispara |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `OP-ROL-01` | `<Actividad>` | `<Rol>` | `<HerramientaProduccion>` | `<Artefacto>` | `E` | `<operación de escritura>` | — |
| `OP-ROL-02` | `<Actividad>` | `<Rol>` | `<HerramientaProduccion>` | `<Artefacto>` | `L` | `<operación de lectura>` | — |
| `OP-APO-01` | `<Actividad>` | `<RolApoyo>` | `<HerramientaComunicacion>` | `<Artefacto>` | `E` | `<operación que dispara>` | `TR-01` |

**Reglas de esta sección**

- `Dispara` referencia el `TR-` cuya operación es el disparador. Si la operación no dispara una transición, se escribe `—`.
- Las transiciones sin operación asociada se completan en los pasos 6 y 7; `—` no significa que no exista transición.
- No se permiten operaciones duplicadas para el mismo rol, actividad, herramienta, artefacto y modo.
- Si un rol necesita una operación que no tiene herramienta declarada, se detiene el paso 4 y se vuelve al paso 3.

---

## 4. Esqueleto de transiciones

| ID | Tipo | Desde | Hacia | Ámbito | Disparador (preliminar) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `TR-01` | handoff | `<Rol>` | `<RolApoyo>` | proceso | `<disparador>` |
| `TR-02` | handoff | `<RolApoyo>` | `<Rol>` | protocolo | `<disparador>` |
| `TR-03` | mutación | `<Rol>` | `<RolApoyo>` | protocolo | Pendiente de completar en el paso 7 |

**Reglas de esta sección**

- **handoff:** la responsabilidad pasa de un rol a otro; puede ocurrir entre actividades (proceso) o dentro de una actividad (protocolo).
- **mutación:** el mismo usuario cambia de rol activo dentro de una sesión. Es un fenómeno de protocolo y se completa en el paso 7.
- El paso 4 solo fija `Desde`, `Hacia`, `Tipo` y `Ámbito`. Los disparadores, guardas y efectos se completan en los pasos 6 y 7.
- Si el proyecto no declara mutaciones, se deja constancia explícita; no se inventan.

---

## 5. Checklist de aceptación

- [ ] **C1. Cobertura rol↔actividad.** Todo rol del catálogo aparece en al menos una actividad y todo rol de una actividad está en el catálogo.
- [ ] **C2. Regla de oro.** Toda actividad tiene al menos un rol y al menos una herramienta de comunicación.
- [ ] **C3. Operación completa.** Toda operación tiene actividad, rol, herramienta, artefacto y modo; todos existen en la ficha del workspace.
- [ ] **C4. Sin huérfanos.** Toda herramienta y todo artefacto declarado se usa al menos una vez, o se marca explícitamente como no usado.
- [ ] **C5. Temporalidad.** La modalidad de cada herramienta coincide con la de la actividad (sincrónica/asincrónica).
- [ ] **C6. Visibilidad.** Un rol externo solo lee o escribe los artefactos permitidos; no accede a los internos.
- [ ] **C7. Segregación de funciones.** Quien produce no aprueba; si hay mutación a un rol aprobador, la guarda lo impide o deriva a otra persona.
- [ ] **C8. Multiplicidad.** Está declarada para cada rol-actividad y es compatible con el quórum, si aplica.
- [ ] **C9. Nombres e IDs.** Los nombres coinciden exactamente con las fichas; los IDs son únicos y no hay operaciones duplicadas.
- [ ] **C10. Fuente única.** `roles.md` no se duplica en la ficha del workspace; la ficha resume y enlaza.

---

## 6. Pendientes de los pasos 6 y 7

- **Paso 6 — proceso:** completar los handoffs de ámbito `proceso` con acciones, disparadores y guardas; agregar el diagrama de procesos.
- **Paso 7 — protocolo:** completar los handoffs y mutaciones de ámbito `protocolo` con estados, disparadores, guardas y efectos; agregar el diagrama de protocolo por actividad.

> Si el paso 6 o 7 necesita una operación, herramienta o artefacto no declarado, se vuelve
> al paso correspondiente y se actualiza este archivo antes de continuar.
