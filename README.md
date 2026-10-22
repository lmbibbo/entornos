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
├─ oficina/                      # proyecto: agencia creativa
│  ├─ oficina.md                 # spec con 4 workspaces completos
│  ├─ roles.md                   # roles y operaciones por herramienta (paso 4)
│  └─ diagramas/
│     ├─ 01-mapa-workspaces.drawio
│     ├─ 02-actividades.drawio
│     └─ 03-actividad-estructura.drawio
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
| [`agents.md`](agents.md) | Metamodelo CSSL: glosario de constructos, matriz de relaciones, reglas de diseño y algoritmo de generación en 5 pasos. |
| [`awareness.md`](awareness.md) | Catálogo de los 19 elementos de awareness con su pregunta relevante, criterio de búsqueda y plantilla de declaración. |

`agents.md` define **cómo se especifica**; `awareness.md` es el catálogo que se
consulta al completar el campo *Awareness* de cada ficha.

### Proyectos

| Proyecto | Dominio | Spec | Estado |
| :--- | :--- | :--- | :--- |
| [`oficina/`](oficina/) | Agencia creativa | [`oficina.md`](oficina/oficina.md) · [`roles.md`](oficina/roles.md) | Completo: 4 workspaces, 8 sesiones, 20 herramientas declaradas, 9 roles, 28 operaciones, 12 objetos. |
| [`proyecto-educativo/`](proyecto-educativo/) | Institución educativa | [`educativo.md`](proyecto-educativo/educativo.md) | Completo: 4 workspaces, 8 sesiones, 15 herramientas. |

---

## Diagramas

| Archivo | Contenido | Páginas |
| :--- | :--- | :--- |
| `oficina/diagramas/01-mapa-workspaces.drawio` | Mapa por espacios (Oficina): 4 columnas con sesiones, herramientas y objetos, una por workspace. | 1 |
| `oficina/diagramas/02-actividades.drawio` | Una página por actividad (Oficina): workspace, herramientas, actividad con protocolo y objetos, y roles con multiplicidad sobre la capa punteada de awareness. | 8 |
| `oficina/diagramas/03-actividad-estructura.drawio` | Primera muestra de esa notación, con una sola actividad. | 1 |
| `proyecto-educativo/diagramas/workspaces-diagrama.drawio` | Mapa por espacios: cada workspace en una columna, con sesiones, herramientas y objetos. | 1 |
| `proyecto-educativo/diagramas/actividades-cssl.drawio` | Una página por actividad: herramientas arriba, roles abajo y relaciones como flechas. | 3 |

Se abren en [app.diagrams.net](https://app.diagrams.net) o con la app de escritorio:
*Archivo → Abrir desde → Dispositivo*. No se sube nada a ningún servidor.

Las ocho actividades de `oficina/diagramas/02-actividades.drawio` siguen la plantilla
[`actividad-template.drawio`](actividad-template.drawio): workspace como círculo,
herramientas en verde, actividad como caja con protocolo y objetos, roles en azul con
multiplicidad `1` y una capa punteada de awareness que envuelve la escena.
`03-actividad-estructura` es la muestra de una sola actividad de la que salió la plantilla.

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
3. Volcar las operaciones de cada rol por herramienta en `roles.md` del proyecto (paso 4).
4. Consultar [`awareness.md`](awareness.md) al declarar la capa de awareness de cada espacio o actividad (paso 5).
5. Generar los diagramas en `diagramas/` y exportarlos.

---

## Pendientes

**Algoritmo CSSL de Oficina (pasos 5 a 7)**
- Paso 5: completar la capa de awareness de `CuraduriaReferencias` (no tiene declaración) y dejar explícita la de `BriefingCreativo` (hoy hereda `Presence` del espacio).
- Paso 6: diagrama de procesos y sección de acciones de proceso en `roles.md`.
- Paso 7: protocolo por sesión y sección de acciones de protocolo en `roles.md`.

**Repositorio**
- Rehacer las tres plantillas base en draw.io con texto editable y notación consistente.
- Mover los SVG de referencia a una carpeta `referencias/`.
