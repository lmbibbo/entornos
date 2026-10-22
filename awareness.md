# Awareness · Catálogo CSSL

**Estándar transversal a los proyectos del repositorio**

El awareness no es una herramienta: es la información contextual que el sistema
expone para que el grupo se coordine y no se aísle. Se declara siempre atado a una
**pregunta concreta**: si no responde a una pregunta de coordinación, es decoración.

---

## 1. Dónde se declara

Un awareness se asocia a una pieza del diseño. El orden de trabajo es:

| Alcance | Qué informa | Momento |
| :--- | :--- | :--- |
| **Espacio** (workspace) | Quiénes están en la sala, qué herramientas están activas, qué densidad hay. | Fase 1 |
| **Actividad** (sesión) | Quién participa, con qué rol, qué está haciendo y sobre qué objeto. | Fase 1 |
| **Proceso** | Cómo avanza el flujo entre actividades y dónde está el cuello de botella. | Posterior |
| **Protocolo** | En qué paso normativo está cada participante y qué se espera de él. | Posterior |

Los dos primeros se documentan primero. Procesos y protocolos se agregan después,
con el mismo catálogo de elementos.

### El alcance no es el nivel

Conviene no mezclar dos ejes:

- **Alcance** — a qué pieza del diseño se declara el awareness: espacio, actividad, proceso o protocolo.
- **Nivel** — desde dónde se observa: entorno, espacio, sesión o artefacto.

Un mismo elemento puede declararse en más de un nivel. `Presence`, por ejemplo:

| Nivel | Pregunta |
| :--- | :--- |
| Entorno | ¿Quién está en la agencia? |
| Espacio | ¿Quién está en `Produccion`? |
| Sesión | ¿Quién está en `BriefingCreativo`? |
| Artefacto | ¿Quién está mirando el `TableroBrief`? |

---

## 2. Catálogo de elementos

Esta tabla es la herramienta de búsqueda: se parte de la pregunta de coordinación
que se quiere resolver y se ubica el elemento que la responde.

| Elemento | Pregunta relevante | Foco |
| :--- | :--- | :--- |
| `Presence` | ¿Quiénes están en el entorno, el workspace, la sesión o el artefacto? | Personas |
| `UserLocation` | ¿En qué lugar (espacio, sesión, artefacto, etc.) se encuentra un usuario determinado? | Lugares |
| `Density` | ¿Qué densidad de usuarios hay en cada lugar del entorno? | Lugares |
| `UserInformation` | ¿Qué información conocemos del usuario? | Personas |
| `Rol` | ¿Qué rol tiene el usuario en cada momento? | Personas |
| `ActivityLevel` | ¿Qué nivel de actividad tienen los usuarios? | Personas |
| `UserAction` | ¿Qué acción está haciendo el usuario? | Personas |
| `PlaceAction` | ¿Qué acción se está haciendo en un lugar del entorno (espacio, sesión, artefacto, etc.)? | Lugares |
| `UserHistory` | ¿Cuál es la historia de acciones de un usuario? | Tiempo |
| `Intentions` | ¿Qué harán los usuarios? | Tiempo |
| `UserBookmarks` | ¿Cuáles son los bookmarks de un usuario? | Personas |
| `Expectations` | ¿Qué acción se considera que hará luego un usuario considerando el estado actual? | Tiempo |
| `Changes` | ¿Qué objetos han cambiado? | Objetos |
| `Objects` | ¿Cuál es el estado de algún objeto? | Objetos |
| `Visibility` | ¿Cuál es la visibilidad de algún usuario? ¿Qué objetos puede ver? | Personas |
| `Abilities` | ¿Qué sabe hacer el usuario? Puede tener que ver con el rol. | Personas |
| `Influence` | ¿Cuál es el campo de influencia del usuario? | Personas |
| `ObjectsUsers` | ¿Qué objetos están siendo usados y por quién? | Objetos |
| `ObjectHistory` | ¿Qué cambios se han realizado sobre el objeto y quién lo realizó? | Objetos |

---

## 3. Cómo encontrar el awareness que necesitás

1. **Formulá la pregunta en tus palabras.** Sin pregunta no hay awareness: «no sé si el director ya revisó la pieza».
2. **Buscá la fila del catálogo** que responde eso. Para el caso anterior: `Objects` (estado), `Changes` (qué cambió) y `ObjectHistory` (quién lo hizo).
3. **Elegí el alcance.** ¿Es información de la sala completa (espacio) o de la tarea en curso (actividad)?
4. **Fijá el nivel.** ¿Se pregunta por el entorno, el espacio, la sesión o un artefacto puntual?
5. **Declarala** en la ficha correspondiente, con la plantilla de la sección 4.

### Atajo por alcance

| Alcance | Elementos típicos |
| :--- | :--- |
| **Espacio** | `Presence`, `Density`, `UserLocation`, `ActivityLevel`, `PlaceAction` |
| **Actividad** | `Rol`, `UserAction`, `ObjectsUsers`, `Changes`, `Visibility` |
| **Proceso** *(posterior)* | `ActivityLevel`, `Expectations`, `UserHistory` |
| **Protocolo** *(posterior)* | `Rol`, `PlaceAction`, `Expectations`, `Changes` |

El atajo es orientativo: sirve para empezar a buscar, no para limitar la elección.

---

## 4. Cómo se declara

| Campo | Contenido |
| :--- | :--- |
| **Elemento** | Nombre exacto del catálogo (`ObjectsUsers`, `Changes`, …). |
| **Pregunta** | La pregunta de coordinación que resuelve, en una línea. |
| **Alcance** | Espacio / Actividad / Proceso / Protocolo. |
| **Nivel** | Entorno / Espacio / Sesión / Artefacto. |
| **Dónde se muestra** | Dónde aparece en la interfaz: barra, avatar, badge, lista, resaltado. |
| **Fuente de datos** | De dónde sale la información: presencia, historial, metadatos del objeto. |

### Ejemplo

| Campo | Contenido |
| :--- | :--- |
| **Elemento** | `ObjectsUsers` |
| **Pregunta** | ¿Quién está editando la pieza en este momento? |
| **Alcance** | Actividad (`CoCreacionPieza`) |
| **Nivel** | Artefacto (`LienzoPieza`) |
| **Dónde se muestra** | Cursores con nombre sobre el lienzo. |
| **Fuente de datos** | Sesión activa del editor colaborativo. |

---

## 5. Reglas

- **Sin pregunta, no hay awareness.** Toda declaración empieza por la pregunta que resuelve.
- **Un awareness por problema.** Si un elemento intenta responder tres preguntas a la vez, se parte en tres declaraciones.
- **El nivel artefacto es el más caro.** `ObjectsUsers`, `Changes` y `ObjectHistory` exigen instrumentar el objeto; se justifican solo si la coordinación sobre ese objeto es crítica.
- **Si un alcance no aplica, se declara como no implementado**, no se deja vacío.
