# entornos

Especificaciones de entornos colaborativos (groupware) en **CSSL** — *Collaborative
Software System Language*: espacios de trabajo, actividades, herramientas, roles y
awareness, con sus diagramas.

Repositorio de documentación: no hay código, hay especificaciones y diagramas.

---

## Mapa del repositorio

```
entornos/
├─ agents.md                     # metamodelo CSSL y algoritmo de diseño
├─ awareness.md                  # catálogo de elementos de awareness (estándar)
├─ actividad-template.drawio      # plantilla de una página de actividad
├─ roles-template.md              # plantilla del paso 4: roles y operaciones
├─ oficina/                      # proyecto: agencia creativa
│  ├─ oficina.md                 # spec con 4 workspaces completos
│  ├─ roles.md                   # roles, operaciones, transiciones y protocolos (pasos 4 y 7)
│  ├─ proceso.md                 # proceso: disparadores, estados y 15 transiciones PR- (paso 6)
│  └─ diagramas/
│     ├─ 01-mapa-workspaces.drawio
│     ├─ 02-actividades.drawio
│     ├─ 03-proceso.drawio
│     └─ 04-protocolos.drawio
├─ proyecto-educativo/           # proyecto: institución educativa
│  ├─ educativo.md               # spec con 4 workspaces completos
│  └─ diagramas/
│     ├─ workspaces-diagrama.drawio
│     └─ actividades-cssl.drawio
└─ *- Base.svg                   # plantillas visuales de referencia
```

---

## Piezas

### Estándares

| Archivo | Qué contiene |
| :--- | :--- |
| [`agents.md`](agents.md) | Metamodelo CSSL: glosario de constructos, matriz de relaciones, reglas de diseño y algoritmo de generación en 7 pasos. |
| [`awareness.md`](awareness.md) | Catálogo de los 19 elementos de awareness con su pregunta relevante, criterio de búsqueda y plantilla de declaración. |
| [`roles-template.md`](roles-template.md) | Plantilla del paso 4: catálogo de roles, asignación por actividad, matriz de operaciones, transiciones y checklist de aceptación. |

`agents.md` define **cómo se especifica**; `awareness.md` es el catálogo que se
consulta al completar el campo *Awareness* de cada ficha. `roles-template.md` es la
plantilla que se copia a `<proyecto>/roles.md` en el paso 4.

### Proyectos

| Proyecto | Dominio | Spec | Estado |
| :--- | :--- | :--- | :--- |
| [`oficina/`](oficina/) | Agencia creativa | [`oficina.md`](oficina/oficina.md) · [`roles.md`](oficina/roles.md) · [`proceso.md`](oficina/proceso.md) | Pasos 1–7 completos: 4 workspaces, 8 sesiones, 20 herramientas declaradas (15 únicas), 9 roles, 77 operaciones atómicas, 12 objetos, 28 declaraciones de awareness, 15 transiciones `PR-` y 50 `PT-`. |
| [`proyecto-educativo/`](proyecto-educativo/) | Institución educativa | [`educativo.md`](proyecto-educativo/educativo.md) | Parcial: 4 workspaces, 8 sesiones, 15 herramientas; falta `roles.md` (paso 4) y awareness (paso 5). |

Cada archivo cubre una capa: `oficina.md` describe espacios y sesiones; `roles.md` es la
fuente única de roles, operaciones, handoffs y protocolos; `proceso.md` es la fuente única
del proceso y explica qué operación de qué rol dispara cada transición.

---

## Diagramas

| Archivo | Contenido | Páginas |
| :--- | :--- | :--- |
| `oficina/diagramas/01-mapa-workspaces.drawio` | Mapa por espacios (Oficina): 4 columnas con sesiones, herramientas y objetos, una por workspace, con el awareness de espacio en la cabecera. | 1 |
| `oficina/diagramas/02-actividades.drawio` | Una página por actividad (Oficina): workspace, herramientas, actividad con protocolo y objetos, roles con multiplicidad y callouts de awareness de espacio, sesión y artefacto; los de artefacto muestran la herramienta que lo opera y el artefacto. | 8 |
| `oficina/diagramas/03-proceso.drawio` | Proceso colaborativo (Oficina): 8 actividades, 3 decisiones, inicio y fin, con las 15 transiciones `PR-`, los retornos punteados y el panel de awareness de proceso; página 2 con la tabla de referencia `PR` · rol → objeto — operación. | 2 |
| `oficina/diagramas/04-protocolos.drawio` | Protocolo por actividad (Oficina): una página por actividad con estados `(Rol) Herramienta->operación()`, decisión de retorno y las 50 transiciones `PT-`; página 9 de referencia del awareness de protocolo. | 9 |
| `proyecto-educativo/diagramas/workspaces-diagrama.drawio` | Mapa por espacios: cada workspace en una columna, con sesiones, herramientas y objetos. | 1 |
| `proyecto-educativo/diagramas/actividades-cssl.drawio` | Una página por actividad: herramientas arriba, roles abajo y relaciones como flechas. | 3 |

Se abren en [app.diagrams.net](https://app.diagrams.net) o con la app de escritorio:
*Archivo → Abrir desde → Dispositivo*. No se sube nada a ningún servidor.

Las ocho actividades de `oficina/diagramas/02-actividades.drawio` siguen la plantilla
[`actividad-template.drawio`](actividad-template.drawio): workspace como círculo,
herramientas en verde, actividad como caja con protocolo y objetos, roles en azul con
multiplicidad `1` y callouts punteados de awareness (espacio, sesión y artefacto)
alrededor de la escena, cada uno con su pregunta, ubicación y fuente; los de artefacto
agregan la herramienta que lo opera y el artefacto concreto.

Los diagramas de proceso y protocolo usan las plantillas `Proceso - Base.svg` y
`Protocolo - Base.svg`: actividades verdes con inicio, fin y decisiones en el proceso;
estados UML con cuerpo de operaciones y transiciones punteadas en el protocolo.

**Exportación:** lienzo 1600×900 (16:9). SVG para slides, PNG con zoom 200–300% cuando
el destino no acepta vectores. Se exporta la página completa, no la selección.

---

## Plantillas de referencia

Tres exports de Google Drawings que sirven como base visual para los tres tipos de
diagrama. **Pendientes de rehacer**: el texto está convertido a curvas, así que no se
puede editar ni buscar.

| Archivo | Tipo | Qué muestra |
| :--- | :--- | :--- |
| `Estructura Entorno- Base.svg` | Estructura | Espacios, actividades, herramientas y participantes, con una acción (`Classroom->enter()`). |
| `Proceso - Base.svg` | Proceso | Flujo entre fases: `Presentación → Clase / Discusión → Examen`, con puntos de decisión. |
| `Protocolo - Base.svg` | Protocolo | Estados con las operaciones que habilita cada uno y sus transiciones. |

---

## Convenciones

- **Workspaces y sesiones:** PascalCase sin espacios ni acentos (`DireccionCreativa`, `BriefingCreativo`).
- **Herramientas:** PascalCase que indique la función (`EditorTextoCompartido`).
- **Roles:** PascalCase en singular (`DirectorDeArte`).
- **Objetos compartidos:** PascalCase, con el archivo en cursiva entre paréntesis (`TableroBrief` (*brief_v02.pdf*)).
- **Specs:** una por proyecto, `<proyecto>.md`, dentro de su carpeta.
- **Diagramas:** `NN-nombre.drawio`, una página por vista.

---

## Cómo trabajar

1. Leer [`agents.md`](agents.md) para el metamodelo y las reglas de diseño (4 fases, 7 pasos).
2. Completar las fichas de workspace en la spec del proyecto (orden: workspaces → sesiones → herramientas → roles).
3. Volcar roles, asignación por actividad y operaciones en `roles.md` del proyecto (paso 4), usando [`roles-template.md`](roles-template.md) y su checklist.
4. Declarar awareness de espacio, actividad, proceso y protocolo según [`awareness.md`](awareness.md) (paso 5).
5. Agregar el proceso (`PR-`) a `proceso.md` y los protocolos (`PT-`) a `roles.md` (pasos 6 y 7), y generar los diagramas en `diagramas/`; exportarlos.

---

## Pendientes

**Proyecto educativo**
- Paso 4: agregar el campo `Roles` a las fichas y crear `roles.md` con la plantilla.
- Pasos 5 a 7: awareness, proceso y protocolo.

**Repositorio**
- Rehacer las tres plantillas base en draw.io con texto editable y notación consistente.
- Mover los SVG de referencia a una carpeta `referencias/`.
