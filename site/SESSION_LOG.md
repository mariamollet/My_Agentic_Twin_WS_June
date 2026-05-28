# Session Log — My Agentic Twin HTML Suite

## Context

Trabajo sobre la suite de HTMLs en
`c:\Users\maria.mollet\Accenture\GSK-GSK PMO - Documents\04_Workshops\Workshop 5_June\HTML test - sin What Comes Next\`.

Archivos principales modificados:
- `agenda.html`
- `Programme Summary.html`
- `Executive Summary.html`
- `sara_dmaic_summary_14 1.html`
- `index.html`

Esta sesión añadió docenas de cambios funcionales y de estilo. Resumen completo
para que cualquier futura sesión pueda continuar sin contexto previo.

---

## 1 · Navegación y títulos de pestaña

- **Quitada la entrada "DMAIC"** del nav en todas las páginas (`index.html`,
  `agenda.html`, `Programme Summary.html`, `Executive Summary.html`,
  `sara_dmaic_summary_14 1.html`). El contenido DMAIC solo se accede vía la
  tarjeta clicable en `agenda.html`.
- Títulos `<title>`:
  - `index.html` → "Home"
  - `Programme Summary.html` → "Programme Summary"
  - `Executive Summary.html` → "Executive Briefing"
  - `sara_dmaic_summary_14 1.html` → "My Problem Solving Twin"

## 2 · agenda.html — enlaces y modales nuevos

### Links a Excel UAT
- "My Mentor Twin" → SharePoint Excel `Leadership_Coach_UAT_Template.xlsx`
  (luego sustituido por modal — ver §3).
- "My Problem Solving Twin" → SharePoint Excel `DMAIC_UAT_Template.xlsx`
  (luego sustituido por modal — ver §3).
- "Requirements list (Excel)" → SharePoint Excel `Master_Requirements&Estimates.xlsx`.
- "Microsite Figma" → `https://my-agentic-twin-2026.figma.site/`.
- "Video WILO" → `Video WILO FINAL.mp4`.
- Bajo "Adoption Plan; Demo Videos; Microsite Figma; Video WILO" añadida
  línea en gris cursiva: *Password: MyAgenticTwin2026*.

### Cambios de texto
- "Demo videos; value case update (hours saved)" →
  "Demo videos; value case update of My Problem Solving Twin and My Meeting Twin".
- "Release 2.0 demos (DMAIC & Meetings)" →
  "Release 2.0 demos (Problem Solving & Meetings)".
- "My RCA Belt Twin" → "My Problem Solving Twin" en toda la agenda.
- "Share feedback from early users" — añadidos sub-items anidados
  "My Mentor Twin 2-week Check-in" y "My Mentor Twin 4-week check-in"
  (con clase `.output-sublist`).
- Headers de la cabecera y celdas de Input column alineadas a la izquierda
  (regla `tbody td:nth-child(3), tbody td:nth-child(4) { text-align:left }`).

### Modal: DMAIC iframe
- `#dmaicModal` con `<iframe src="sara_dmaic_summary_14 1.html">`.
- "My Problem Solving Twin" abre este modal.

### Modal: Adoption Plan Gantt
- `#adoptionPlanModal` con CSS completo de `.ap-*` (gantt 18 semanas).
- Lanes: Foundations, Agent Testing, Ambassador Rollout, Community.
- Abierto desde "Adoption Plan" en columna Inputs.

### Modal: My Mentor Twin UAT results
- `#mentorUatModal` (clase `.uat-card`).
- Título "My Mentor Twin - UAT results", subtítulo
  "16 requirements tested across 5 capability areas".
- 4 stats (Pass 12·75%, Partial 3·19%, Fail 0·0%, Not Tested 1·6%).
- 5 capability bars: Focus & Execution, Performance, Communication,
  Team Growth, Other capabilities.
- "Why the partials?" con texto de Workday/Planner.
- Botón pastel arriba derecha: "View detailed results →" → Excel.

### Modal: My Problem Solving Twin UAT results
- `#psUatModal`.
- Título "My Problem Solving Twin — UAT results", subtítulo
  "47 requirements tested across 10 sections".
- Overall 60% — "Considered as partial".
- 3 stats (Pass 28·60%, Fail 2·4%, Not Tested 5·36%), altura igualada
  a Mentor Twin (`uat-status-grid--3` con `grid-auto-rows:110px`).
- 10 sections en grid 5 columnas: Historical DMAICs Agent, Getting Started,
  Define Phase, Measure Phase, Analyse Phase, Improve Phase, Control Phase,
  Process Map Agent, Charts Generator Agent, General Behaviours.
- "Why the fails?" con texto sobre Team field + root cause confirmation en
  v1 reforzados en v2 Copilot Studio.
- Botón → Excel `DMAIC_UAT_ Red Training KPI DMAIC.xlsx`.

### Modal: Mentor Twin 2-week Check-in dashboard
- `#mentorCheckin2Modal`.
- 5 preguntas: usage frequency (donut), capabilities (aligned bars),
  rating 4.25/5 (stars + level bars), Q4 free-text (4 quotes), Q5
  free-text (4 quotes).

### Modal: Mentor Twin 4-week Check-in dashboard
- `#mentorCheckin4Modal`.
- 16 preguntas estilo Microsoft Forms:
  - Q1 donut usage, Q2 aligned bars capabilities, Q3 rating 3.50/5,
    Q4 donut 1:1s, Q5 donut awareness, Q6 donut communication,
    Q7 donut single-segment (100% I haven't conducted), Q8 donut planning,
    Q9 donut follow-ups, Q10 donut single-segment (Too early to say),
    Q11–Q13 aligned bars time spent (preparing week / 1:1s / interviews),
    Q14 rating 4.00/5, Q15 free-text (single most useful),
    Q16 free-text (would change/add).
- Paleta de colores cálida alineada con naranja GSK
  (#D14E1F · #F36633 · #F49B6E · #B85829 · #8B5A3C · #C9A07C · #4A5568 · #6E8B8E).
- Layout en grid 2 columnas (`.dash-grid`), `display:flex; flex-direction:column`
  en cada `.dash-card` para centrar verticalmente cuando una card es más corta.

### Modal: Twinny functionalities (Navigator + Accelerator)
- `#twinnyModal` con dos columnas:
  - **Twinny as My Agentic Twin Navigator** (Router Agent, Agent Marketplace,
    Programme Guide).
  - **Twinny as Agent Accelerator** (4 pasos: Idea Receival, Complexity Screening,
    Training Buddy Simple, Routed to Org. Model Medium/Complex).
- Botón "Discover more →" en columna Accelerator que abre el `#tflow-modal`.

### Modal: Twinny Flow (Accelerator Section)
- `#tflow-modal` + `#tflow-detail-modal` importados de
  `HTML test\from_ambition_to_delivery.html`.
- CSS completo del flow (`.tflow-overlay`, `#tflow-modal *`, todas las clases
  `.fc`, `.route-*`, `.split-*`, `.pip-*`, etc.).
- JS handlers `openTwinnyFlow`, `openDetailPanel`, click/keyboard handlers en
  `.fc[data-detail]`. Envueltos en `DOMContentLoaded` para evitar el bug
  de "tflowModal is null".
- **Colores morados eliminados** — `--complex`, `--complex-soft`, `--complex-line`
  ahora son los mismos que `--orange-*` (renaming via var inheritance).
  Inline `#6b3fa0`, `#c4a8e6`, `#f3eefb`, `#6b21a8`, `#f3e8ff`, `#f8f4fd`
  reemplazados por equivalentes naranja.

### Modal: Development Pipeline Backlog (panel del tflow-detail)
- Refinado tras múltiples iteraciones:
  - `td-card--wide` max-width `min(1320px, 95vw)`, padding 26/24.
  - `pip-layout` grid `140px 18px minmax(0,1fr) 18px 140px`, `align-items:stretch`
    (side-boxes igualan altura de la tabla).
  - Tabla con `table-layout:fixed` + `<colgroup>` con anchos explícitos
    (19% · 15% · 10% · 10% · 10% · 11% · 12% · 13%).
  - Headers: `font-size:9.5px`, `white-space:normal`, `text-align:center`.
  - Celdas: `font-size:11px`, padding 8×6, `overflow-wrap:anywhere`.
  - Pills cpill/spill: `font-size:9px`, `white-space:nowrap`.
  - `tdPop` keyframe definido localmente (sustituye `wn-pop` que no existía).
  - Animación de filas: `rowFade` (solo opacity, sin translateY) — pero
    luego desactivada (rows opacity:1 desde el inicio para evitar flicker).

### Modal: Rapid UAT
- `#rapidUatModal` abierto desde el link "R2.0 UAT for rapid feedback".
- 2 cards: "Session with Morgan · Thursday, 4 June · 1.5h" (My Meeting Twin)
  y "Session with Toni · Thursday, 4 June · 1.5h" (My Problem Solving Twin).
- Footer banner: "UAT deadline — 5 June 2026 — feedback consolidated…".

### Modal: Roadmap (iframe)
- "Development timelines & team proposal" abre `#roadmapModal` con
  `<iframe src="Programme%20Summary.html?view=roadmap">`.
- Tamaño 1500px max / 92vw / 90vh, padding overlay 12px.

## 3 · Programme Summary.html

### Cambios estructurales
- Eliminado el bloque "Reinventing an employee's week" + persona banners
  + nota final.
- Priority cards (Meetings, Problem Solving, Become a Better Leader):
  - "Estimated Value: X% of time reduction" eliminado de las 3 tarjetas.
  - Todas con "What gets reinvented" (en lugar de DMAIC phases automated /
    Leadership rhythm).
  - Listas actualizadas con los items dictados por el usuario.
  - `.priority-desc { min-height:130px; flex-grow:0 }` para que los headers
    "What gets reinvented" empiecen a la misma Y en las 3 tarjetas.
- Problem Solving: "Estimated Value: 40% of time reduction" (luego eliminado).

### View-roadmap query param
- Añadido en `<head>`:
  - CSS: `.view-roadmap .site-header, .hero, .section-ambition,
    .section-strategy, .site-footer, .wip-badge { display:none !important }`.
  - Script: si `?view=roadmap`, añade clase `view-roadmap` al `<html>`.
- Permite incrustar Programme Summary en iframe mostrando solo la sección
  "What Comes Next" (gantt + Programme Enablers), con todos los modales del
  gantt funcionando normalmente.

### orgModelModal (New Organisation Model)
- Grid `.om-diagram` ajustado: `0.85fr 0.7fr 160px 1.3fr 1fr` (lado-label
  ancho, squads más estrecho, funnel 160px).
- `.om-side-label`:
  - `display:flex; flex-direction:column; align-items:center;
    justify-content:center; gap:14px`.
  - Botón "Check my journey" con avatar `persona1.png` (24×24 circular) +
    texto + chevron, estilo pastel (border + bg `--ns-accent-soft`,
    color `--ns-accent-dark`).
  - Texto y botón agrupados en el centro vertical, sin huecos.
- **Funnel reemplazado por factory.png**:
  - `factory.png` clicable (max-width 140px) que abre `afeModal`.
  - SVG funnel original mantenido detrás con `opacity:0.25` como decoración.
  - Símbolo "+" arriba derecha de la imagen.
  - Label "My Agentic Twin Accelerator Framework Execution" debajo,
    `margin-top:-20px`, `font-size:9.5px`, `max-width:140px` (cae dentro
    del área del funnel).

### journeyModal — 7-step Agent Accelerator Framework
- Nuevo `#journeyModal` con la `.framework` completa (stepper + 7 pasos):
  1. Opportunity Detection
  2. Catalogue & Twinny (antes "Marketplace & Twinny")
  3. Complexity & Build
  4. Clearing House
  5. Publish
  6. Adoption & Feedback
  7. Value Capture
- Title format `.om-title` / `.om-subtitle` (mismo formato que orgModelModal):
  "My Agentic Twin - <span class='accent'>Agent Accelerator Framework</span>"
  + subtítulo de gobernanza.
- "Marketplace" → "Catalogue" en todo el journey.
- JS `initFramework(root)` + handler `window.initFrameworkOnce()` que
  inicializa el stepper la primera vez que se abre.
- Escape handler incluye `journeyModal`.
- **`.framework-path.complex`**: border y label color cambian de `#6b3fa0`
  (lila) → `var(--gsk-orange-dark)` (naranja oscuro).

## 4 · Executive Summary.html

### Cambios estructurales
- Adoption Plan modal añadido (clicable desde "Adoption Plan definition").
- Microsite in Figma — link a `https://my-agentic-twin-2026.figma.site/`.
- Sección Potential Value reordenada:
  1. "We don't just deliver hours back…" + 12 value-items (`.value-grid`,
     `margin-bottom:18px`).
  2. "Estimated annual value per reinvented use case." + 4 value-cases.
  3. "My Agentic Twin embeds AI into daily workflows…" (final).
- 4 cards de value-cases ahora usan `.value-case-extra` (mismo estilo que
  "Additional hours + £ savings", **sin italic** — se quitó del CSS).
- My Problem Solving Twin: "40% of time reduction".

### Roadmap modal — sustituido por iframe
- El `#roadmapModal` antes tenía el gantt inline (clases `ns-tl-*`).
- Ahora es un `.dmaic-modal` con `<iframe
  src="Programme%20Summary.html?view=roadmap">` (CSS `.dmaic-modal*`
  añadido al `<style>`).
- Asegura sincronización automática con Programme Summary.

## 5 · sara_dmaic_summary_14 1.html (DMAIC page)

### iframe-aware
- Script en `<head>`: si `window.self !== window.top`, añade clase
  `in-iframe` al `<html>`.
- CSS: `.in-iframe .site-header { display:none !important }` y
  `.in-iframe .wrap { padding-top:24px !important }`.
- Cuando se carga desde el modal de agenda, no muestra la barra de navegación.

### Refactor completo de la página
- Tab "01 Status by category" eliminado (solo queda 1 panel).
- Eyebrow: "Requirements and value assessment" (formato `Agentic Strategy`
  de Programme Summary: Inter 12px, letter-spacing 2.5px, naranja GSK).
- H1: "My Problem Solving Twin" (formato `section-title` de Programme Summary:
  Inter 30px, weight 600, charcoal, letter-spacing -0.3px).
- Subtítulo: "From hours of manual work to a guided, evidence-led problem
  solving flow." (formato `section-lead`).
- "Phases" en formato `.sub-label` de Programme Summary (Inter 13px, naranja).
- Phase boxes:
  - `border-radius:12px`, hover lift (-3px, sombra, borde naranja).
  - "PHASE 01" badge posicionado absolute arriba a la derecha,
    `font-size:9px`, padding 2×7.
  - `phase-name` `font-size:15px`.

### Paleta de colores forzada a naranja + grises
- Variables CSS redefinidas:
  - `--green: #F36633`, `--amber: #F36633`, `--blue: #F36633`,
    `--red: #475569` (slate gris).
- Backgrounds:
  - `#e6f0e8`, `#eef7f0`, `#f3ebd6`, `#fdfaf2`, `#eef4f9`, `#fdf8ee`,
    `#f3e0e0` → `#FEF2EC` (naranja tenue).
- "Blue dot" (in-progress): `var(--blue)` → `#cbd5e1` (gris claro).

### Bloque "Requirements coverage by version"
- 3 cards separadas (gap 24px, sin divisores) con borde gris fino,
  borde izquierdo naranja 4px, border-radius 12px, sombra suave, hover lift.
- Eyebrows simplificados ("Covered in **V1**" / "New in **V2**" /
  "New and Refined in **V3**" con V1/V2/V3 en naranja).
- Sub-textos eliminados ("V1 = Complete", "V1 OoS/Blocked → V2 Complete…",
  "3 blocked (deferred)").
- Pills "% time saved" posicionadas absolute arriba derecha, color unificado
  (`#FEF2EC` fondo / `var(--accent)` texto).
- V3: línea italic gris "3 new + 3 refining V2 features" entre el número y
  la pill.
- Spacer invisible en V2 para que el "▾ Click to see where savings come from"
  esté a la misma altura que en V3.

### Tabla "All requirements — V2 scope (unified view)"
- Cabecera unificada en una tabla separada (encima de "In Progress").
- 5 columnas con `table-layout:fixed` y anchos explícitos (14% · 10% · 18%
  · 38% · 20%).
- Wrapper `.unified-reqs` con `border-radius:10px`, `overflow:hidden`,
  hover en filas (fondo `#FFFAF7`).
- Headers formato agenda (Inter 11px, letter-spacing 1.8px, naranja GSK,
  fondo `#FFF8F4`, centrados).
- Celdas td: `text-align:left !important`.
- Iconos SVG sustituyen emojis en labels:
  - 🔵 In Progress → reloj (círculo + manecillas)
  - ✅ Complete → checkmark
  - 🟡 V3 — Blocked → círculo tachado
- Label V3 Blocked: `background:#FEF2EC` (igual que Complete).
- "V3 improvement" → "V3 refinement".
- "Blocked → V3" → "Blocked".
- Filas V3 Blocked: fondo blanco (quitado `background:#FEF2EC` por fila).
- Badge "at risk" en naranja (`background:#FEF2EC; color:var(--accent)`).
- `.feat-badge*` sin fondo ni padding (texto monospace 12px gris oscuro,
  estilo igual que la columna Req).

### Tabla V3 development timeline and blockers
- Restaurada desde `sara_dmaic_summary_14 1-AP1630899695152.html`
  (se había eliminado por error junto con tabs 2/3/4).
- Wrapper `.v3-timeline-wrap` con `border-radius:10px; overflow:hidden`
  (borde gris quitado posteriormente).
- Tabla `.tl-table` font 12.5px, sub-textos 12px (achicada para igualar la
  unified table).
- Headers `text-align:center`, fondo `#FFF8F4`, Inter 11px, letter-spacing
  1.8px, naranja GSK.
- Strong de nombres ("BELTIX Metadata Tagging" etc.) con formato `topic-name`
  (Inter 14px, weight 600, charcoal, line-height 1.35).
- Col "Est. effort" `width:130px`.
- `dep-tag`: texto explicativo va en `<br>` (línea aparte, no al lado).
- `.blocker-tag` (PENDING): `background:#FEF2EC; color:var(--accent)`.

## 6 · index.html / roadmap-gantt.html

- index.html: nav simplificado (sin DMAIC), título "Home".
- roadmap-gantt.html: sin cambios significativos.

---

## Recordatorios / decisiones de diseño

- **Paleta**: el usuario rechaza explícitamente colores no naranja en las
  páginas (azul, verde, amarillo, lila/morado). Toda nueva UI debe usar
  variantes del naranja GSK + grises neutros para contraste.
- **Excel links**: el usuario prefiere abrir el preview de SharePoint
  Online (`:x:/r/...`) en pestaña nueva, NO el protocolo `ms-excel:` ni
  descarga directa.
- **Animaciones**: para tablas, animaciones de filas que usen `translateY`
  pueden causar flicker (las TR no transforman bien). Usar solo opacity o
  desactivar.
- **Modales iframe**: cuando una página se cargue en iframe, debe ocultar
  su propia nav. Patrón: `if (window.self !== window.top)
  document.documentElement.classList.add('in-iframe')` + CSS condicional.
- **Source of truth del gantt**: el gantt "What Comes Next" vive en
  Programme Summary. Agenda y Executive Briefing lo embeben vía
  `?view=roadmap` para evitar duplicación.
- **Fuente original del Twinny flow**: el HTML del `#tflow-modal` /
  `#tflow-detail-modal` se importó de
  `c:\Users\maria.mollet\Accenture\GSK-GSK PMO - Documents\04_Workshops\
  Workshop 5_June\HTML test\from_ambition_to_delivery.html`.

## Verificación

1. Abrir cada HTML en navegador moderno (Chrome / Edge).
2. Probar todos los enlaces clicables de la columna Input en agenda:
   - "My Mentor Twin" → modal UAT (12·3·0·1 Workday/Planner).
   - "My Problem Solving Twin" en R1.0 → modal UAT (28·2·5 Why fails).
   - "My Problem Solving Twin" en Demo videos → DMAIC iframe.
   - "Twinny's functionalities" → Navigator + Accelerator → Discover more
     → flow modal completo (Simple/Complex/Pipeline) → click cards →
     paneles detalle (screening, value, pipeline backlog).
   - "My Mentor Twin 2-week Check-in" / "4-week check-in" → dashboards.
   - "Adoption Plan" → modal gantt.
   - "Microsite Figma" / "Video WILO" → pestañas nuevas.
   - "R2.0 UAT for rapid feedback" → modal sessions.
   - "Requirements list (Excel)" → SharePoint.
   - "Development timelines & team proposal" → roadmap iframe.
3. En Executive Briefing: "View Roadmap →" abre el mismo iframe del roadmap.
4. En Programme Summary: scroll a "What Comes Next" → click en cualquier
   bar del gantt → modales abren (Org Model con factory clicable + Check
   my journey, Adoption Plan, Accelerator Framework Execution).
5. En el journey modal: navegación con Prev/Next y click en steppers
   funciona, paso 1 al abrir.
6. En la página DMAIC: comprobar que no hay restos de azul / verde /
   amarillo / lila / morado. Las dos tablas mismo aspecto. V3 timeline
   completa y legible.
