# DESIGN.md — Qudox

> Sistema de marca de **Qudox** para generación de presentaciones (PPTX) por agentes de IA. Este archivo es la fuente de verdad. Si vas a producir un deck para Qudox o sus clientes, **leelo entero antes de generar el primer slide** y respetalo al pie de la letra. Si una decisión visual no está aquí, NO la inventes: preguntá.

---

## 1. Identidad

- **Marca:** Qudox — Growth Marketing Company AI First.
- **Tono:** estratégico, tecnológico, corporativo, creativo, consultivo, claro, dinámico, confiable.
- **Tagline de cierre:** *Together, we power growth.* (ES: *Juntos potenciamos el crecimiento.*)
- **Lo que entregamos:** ecosistemas de crecimiento que conectan estrategia, creatividad, data, medios, tecnología e IA.

---

## 2. Sistema de color — paleta de presentaciones

Las presentaciones de Qudox **usan un sistema verde extendido**, no la paleta cyan/yellow del producto digital. El verde es el lenguaje cromático de las presentaciones; cyan/yellow se reservan para producto.

### 2.1 Tokens principales

```
PRIMARIO
qx-green             #16B87A   verde Qudox · color institucional de presentaciones
qx-green-bright      #38E08C   verde brillante · acento de energía y resaltes
qx-yellow-green      #B6E02A   verde-amarillo · acentos puntuales del patrón
qx-yellow-green-soft #C5D83A   verde-amarillo apagado · variante del patrón

OSCUROS (fondos)
qx-dark              #0D1512   fondo principal de slides oscuras
qx-dark-deep         #06241B   verde muy oscuro · fondo de portada
qx-dark-forest       #1F4035   verde oscuro forest · capas de portada/cierre
qx-dark-mid          #26322C   verde grisáceo oscuro · paneles, separadores
qx-dark-warm         #2C3832   neutro oscuro · variante de fondo

NEUTROS
qx-ink               #1F2937   texto principal sobre claro
qx-ink-soft          #3A463F   texto secundario sobre claro
qx-ink-muted         #5D6B63   texto terciario / captions
qx-white             #FFFFFF   blanco · fondo principal de slides claras
qx-paper             #E5E5DD   crema apagado · fondos muy puntuales
qx-tint-green        #E7F3EC   verde clarísimo · tints de superficie
```

### 2.2 Reglas de aplicación

- **Slides claras (mayoría del deck):** fondo `#FFFFFF`, texto principal `#1F2937` o `#0D1512`, eyebrow y resaltes en `qx-green #16B87A`.
- **Slides oscuras (portadas, separadores, cierres):** fondo `#0D1512` o `#06241B`, texto principal `#FFFFFF`, números y acentos en `qx-green-bright #38E08C`.
- **Cyan `#00FFEF` y Yellow `#EAFF00` no se usan en presentaciones de Qudox.** Aparecen sólo en producto digital (web/app/UI). Si Claude duda, **elige verde**.
- **Rojos / colores externos:** únicamente cuando el cliente o el dato lo exigen (ej. mostrar paletas de marcas competidoras en un benchmark). Nunca como acento institucional.

### 2.3 Proporción típica en un slide

- 60–70% fondo (blanco o dark) + estructura.
- 20–25% texto.
- 10–15% acento verde (eyebrow, números, resaltes, callouts, patrón de footer).

---

## 3. Tipografía

Dos familias, sin excepción.

### 3.1 Familias y pesos

| Familia              | Estilo dominante       | Uso                                                       |
| -------------------- | ---------------------- | --------------------------------------------------------- |
| **Newsreader**       | **SemiBold (600) Italic** | Display: títulos de portada, separadores, títulos editoriales y números grandes. Es la firma de marca. |
| **Manrope**          | Regular / Medium / **Bold (700)** | Todo lo demás: eyebrows, subtítulos, body, labels, captions, datos, tablas. |

Carga (si renderizás web/HTML adjunto):

```html
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,wght@1,600&family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

### 3.2 Escala (puntos) — basada en los decks reales

| Rol                                        | Familia                  | Tamaño    |
| ------------------------------------------ | ------------------------ | --------- |
| Título de portada                          | Newsreader SemiBold Italic | **88–96 pt** |
| Título de separador de sección             | Newsreader SemiBold Italic | **60–72 pt** |
| Número de sección (01, 02…)                | Newsreader SemiBold Italic | **54–60 pt**, color `qx-green-bright` |
| Título principal de slide de contenido     | Newsreader SemiBold Italic | **37–44 pt** |
| Slide de cierre / frase de impacto         | Newsreader SemiBold Italic | **40–54 pt** |
| Subtítulo grande de body                   | Manrope Bold             | **24–30 pt** |
| Subtítulo / item de TOC                    | Manrope Bold             | **20–24 pt** |
| Body                                       | Manrope Regular          | **17–19 pt** |
| Eyebrow / overline (MAYÚSCULAS)            | Manrope Bold             | **12–14 pt**, tracking `0.12em` |
| Labels de tablas / captions                | Manrope Bold             | **13–16 pt** |
| Caption / nota al pie                      | Manrope Regular          | **11–13 pt**, color `qx-ink-muted` |

### 3.3 Reglas tipográficas

- **Newsreader siempre va en italic.** Nunca upright. Es la firma visual de Qudox.
- **Newsreader es el momento editorial, no el default.** Una o dos veces por slide como máximo (típicamente sólo el título). El resto es Manrope.
- **Truco editorial admitido:** dentro de un título en italic, una palabra en **upright** (Newsreader normal) crea énfasis sin cambiar de peso. Ej.: *Together, we* **power** *growth*. Usar con criterio, no en cada slide.
- **Eyebrows en mayúsculas** con tracking amplio (~`0.12em`), color `qx-green #16B87A` sobre claro o `qx-green-bright` sobre oscuro.
- **Nunca usar tipografías externas** (ni Calibri, ni Aptos, ni Arial decorativa). Si una se cuela en una tabla generada automáticamente, reemplazarla por Manrope.
- **Italic en Manrope = prohibido para texto largo.** Si necesitás énfasis, usá Manrope Bold o cambiá a Newsreader Italic puntualmente.

---

## 4. Anatomía de slides — tipos canónicos

Cualquier deck de Qudox se compone de combinaciones de estos 7 tipos. Claude debe identificar qué tipo corresponde a cada slide antes de empezar a maquetarlo.

### 4.1 Tipo `cover` — Portada

**Fondo:** dark con textura orgánica verde (mezcla de verdes oscuros + brillantes con grano/ruido, capas líquidas). Si no se puede generar la textura, usar fondo sólido `#06241B` con un patrón de triángulos verdes superpuesto.

**Estructura:**
- Logo `QUDOX` (versión blanca, con descriptor) centrado en el tercio superior.
- Título grande **Newsreader SemiBold Italic 88–96pt, blanco**, centrado horizontalmente, posicionado en el centro vertical.
- Subtítulo en **Manrope Regular 18–22pt blanco**, debajo del título, 2–3 líneas máx., centrado.
- (Opcional) logo del cliente o un triángulo verde con marca en el tercio inferior.

**Ejemplo de contenido:**
```
QUDOX [logo blanco]

Fase 2 - Believe It   ← Newsreader Italic 96pt

Estrategia de Marca · Insights de marca, Buyer Personas,
Brand Ladder, Brand Voice Chart y Propuesta de Valor.
```

### 4.2 Tipo `toc` — Índice / Contenido de la presentación

**Fondo:** blanco `#FFFFFF`.

**Estructura:**
- Eyebrow superior izquierda: `CONTENIDO DE LA PRESENTACIÓN` o `ÍNDICE`, Manrope Bold 12–14pt, tracking amplio, color `qx-ink-muted`.
- Título principal: **Newsreader SemiBold Italic 37–44pt**, color `#0D1512`, alineado a la izquierda, debajo del eyebrow.
- Lista numerada en grid de **2 columnas** (3 columnas máx. si son más de 6 ítems). Cada ítem:
  - Número en **Newsreader SemiBold Italic 37pt color `#16B87A`** (ej. `01`).
  - Línea divisoria fina horizontal (`#0D1512` 1px) arriba de cada ítem.
  - Título del ítem en **Manrope Bold 20–24pt**.
  - Descripción breve en **Manrope Regular 17–18pt** color `qx-ink-soft`, 1 línea.
- Footer: logo `QUDOX` (versión negativa/positiva apropiada) + banda de patrón verde (ver sección 5).

### 4.3 Tipo `section-divider` — Separador de sección

**Fondo:** dark `#1F2937` o `#0D1512`.

**Estructura:**
- Número grande de sección: **Newsreader SemiBold Italic 54–60pt color `qx-green-bright #38E08C`**, alineado a la izquierda, posición vertical centro-alto.
- Título de la sección debajo: **Newsreader SemiBold Italic 60–72pt color blanco**.
- Subtítulo en **Manrope Regular 18–22pt color blanco**, 1–2 líneas.
- Footer: logo `QUDOX` (versión blanca) abajo-izquierda + patrón decorativo de líneas finas (chevrons/curvas en tonos verde brillante, cyan apagado, yellow apagado) en el tercio inferior.

### 4.4 Tipo `content-2col` — Contenido principal (texto + imagen)

**Fondo:** blanco `#FFFFFF`.

**Estructura:**
- **Header (ocupa ~20% superior):**
  - Eyebrow: nombre de la sección, Manrope Bold 12–14pt MAYÚSCULAS, color `qx-ink-muted` o `qx-green`.
  - Título: **Newsreader SemiBold Italic 37–44pt**, color `#0D1512`.
  - Línea divisoria horizontal fina debajo del título, color `qx-green #16B87A`, 1px, ancho ~50% del slide.
- **Columna izquierda (~55%):**
  - Sub-eyebrow (ej. `INSIGHT 1`): Manrope Bold 13–14pt MAYÚSCULAS, color `qx-green`.
  - Headline del insight: **Manrope Bold 24–30pt**, color `#0D1512`, 2–3 líneas.
  - Párrafo body: Manrope Regular 17–18pt, color `qx-ink`, line-height ~1.4, 3–6 líneas.
  - **Callout box** opcional al final: fondo blanco con **borde izquierdo grueso verde** (3–4px `qx-green`), padding generoso, contiene una `<strong>Frase corta en Manrope Bold verde</strong> seguida de descripción en Manrope Regular`.
- **Columna derecha (~40%):**
  - Imagen con esquinas redondeadas (`border-radius` ~16–24px).
- **Footer:** logo QUDOX abajo-izquierda + banda de patrón verde (~10% altura del slide).

### 4.5 Tipo `content-grid` — Grid de comparación / dimensiones

**Fondo:** blanco o dark según corresponda.

**Estructura:**
- Header igual a `content-2col` (eyebrow + título Newsreader Italic).
- Grid de 3–4 columnas con:
  - Título de columna en **Newsreader SemiBold Italic 22–28pt** color verde (sobre claro) o blanco (sobre oscuro).
  - Sub-labels en Manrope Bold MAYÚSCULAS 11–13pt tracking amplio, color `qx-ink-muted`.
  - Body en Manrope Regular 16–18pt.
- Espaciado entre columnas: ~24–32pt.

### 4.6 Tipo `data-callout` — Stat / dato destacado

**Fondo:** dark o claro.

**Estructura:**
- Eyebrow pequeño.
- Número o dato en **Manrope Extra Bold 72–120pt**, color `qx-green-bright` sobre dark, `qx-green` sobre claro. Letter-spacing ligeramente negativo.
- Caption debajo en **Manrope Regular 16–18pt**, color con menos énfasis.
- Acompañado de gráfico o ilustración si aplica.

### 4.7 Tipo `closing` — Cierre / frase de impacto

**Fondo:** dark con textura verde (igual que portada).

**Estructura:**
- Frase central única, en **Newsreader SemiBold Italic 40–54pt blanco**, centrada vertical y horizontalmente.
- Eyebrow opcional debajo: nombre de fase + bullets de secciones cubiertas, Manrope Regular 13–15pt blanco con `qx-green` para el nombre del proyecto.
- Logo QUDOX al pie centrado o abajo-izquierda.

**Ejemplo de contenido:**
```
Movilidad con respaldo experto.   ← Newsreader Italic 48pt blanco

FASE 2 — BELIEVE IT
Insights · Buyer Personas · Brand Ladder · Brand Voice · Propuesta de Valor

QUDOX [logo]
```

---

## 5. Patrón y elementos gráficos

El "patrón Qudox" es uno de los activos visuales más reconocibles. Se construye con:

- **Triángulos verdes** (chevrons apuntando hacia arriba) de distintos tamaños y rotaciones.
- **Texturas líquidas/orgánicas verdes** con grano puntillista (efecto granito o splatter).
- **Líneas finas** rectas y curvas en tonos `qx-green-bright`, `qx-yellow-green`, y cyan/yellow apagados — sólo en slides oscuras.

### 5.1 Banda de patrón en footer (slides claras)

Una banda horizontal en el borde inferior, ~80–100pt de alto, con:
- Logo `QUDOX` (versión negativa sobre fondo verde texturizado) a la izquierda.
- Serie de 4–6 fragmentos de triángulos verdes mezclando: textura granito verde oscuro, verde brillante sólido, verde muy oscuro, verde-amarillo. Cada fragmento ocupa un ancho similar y juntos cubren todo el borde inferior.

### 5.2 Pattern de fondo en slides oscuras

Líneas finas decorativas dispersas en el tercio inferior: chevrons/curvas en `qx-green-bright`, cyan suave (`#3A4A50`), yellow suave (`#5A5A30`). Sutiles, no compiten con el texto.

### 5.3 Texturas de portada y cierre

Mezcla de:
- Fondo base `#06241B`.
- Capas de `#16B87A` y `#38E08C` con opacidad.
- Triángulos grandes superpuestos.
- Textura puntillista/granito en `#B6E02A` (puntos amarillo-verde dispersos).

Si no es posible recrear la textura programáticamente, usar una imagen pre-renderizada como fondo de portada, o fondo sólido `#06241B` con triángulos vectoriales superpuestos.

### 5.4 Reglas del patrón

✅ **Sí:**
- A sangre completa (full bleed) en el footer de slides claras.
- En portadas y cierres como atmósfera de marca.
- En section dividers, sutil en el tercio inferior.

❌ **No:**
- Detrás de textos largos.
- Recoloreado fuera del sistema verde.
- Saturando el slide (compite con contenido).
- En slides de data densa / tablas.
- Sobre fondos de color sólido brillante.

---

## 6. Logo

### 6.1 Versiones

- **`QUDOX` horizontal con descriptor "Growth Marketing Company"** — firma primaria. Default en TOC, content y closing slides.
- **`QUDOX` versión negativa (blanca)** — sobre fondos oscuros y portadas.
- **`QUDOX` versión positiva (negra/dark)** — sobre fondos claros.
- **Símbolo Q solo** — avatares, favicons, marcas de agua sutiles.

### 6.2 Posición típica en slides

- **Cover:** centrado horizontalmente, tercio superior.
- **TOC, content, content-grid:** abajo-izquierda, integrado a la banda de footer.
- **Section divider, closing:** abajo-izquierda o abajo-centro.

### 6.3 Reglas

- Área de respeto: 1 X (altura del símbolo Q) en los cuatro lados.
- Tamaño mínimo: 140 px / 1" en slide.
- ❌ No deformar, no rotar, no recolorear, no aplicar sombras.

---

## 7. Estructura típica de un deck Qudox

Un deck completo sigue esta secuencia (adaptable):

1. `cover` — Portada con título y subtítulo del proyecto.
2. `toc` — Contenido de la presentación.
3. `section-divider` — `01` + Nombre de la primera sección.
4. `content-2col` × N — Slides de contenido de esa sección.
5. (Repetir 3-4 para cada sección.)
6. `closing` — Frase de cierre conectada a crecimiento.

**Regla de oro:** cada sección comienza con un `section-divider` numerado. Los números (`01`, `02`, `03`…) son parte de la firma visual.

---

## 8. Principios de slide (no negociables)

1. **Una idea fuerte por slide.** Si un slide tiene dos titulares, dividilo.
2. **Títulos claros y contundentes.** No frases vacías como "Análisis del mercado": preferir "El mercado pide claridad, no más opciones."
3. **Textos cortos.** Máx. 4–6 líneas de body por columna. Si hay más, partir en dos slides.
4. **Data visual antes que data saturada.** Máximo 3–5 datos por slide.
5. **Uso intencional del patrón.** Footer en todo slide claro de contenido. Atmósfera en portada y cierre. Resto: sin patrón.
6. **Contraste alto.** Si dudás si se lee, no se lee.
7. **Ritmo dark → light → dark.** Alternar tonos a lo largo del deck para mantener energía.
8. **Cierre siempre conectado a crecimiento.** El último slide referencia el propósito de Qudox.

---

## 9. Identidad verbal — voz en slides

### 9.1 Tono

Qudox habla con **claridad estratégica, seguridad corporativa, sensibilidad creativa y visión tecnológica**. Suena experto sin sonar rígido, cercano sin sonar informal.

### 9.2 Sí / No

| ✅ Sí                                    | ❌ No                                  |
| ---------------------------------------- | -------------------------------------- |
| Estratégicos y orientados a negocio      | Genéricos o decorativos                |
| Claros y estructurados                   | Confusos o improvisados                |
| Creativos con propósito                  | Creativos solo por estética            |
| Tecnológicos y AI First                  | Técnicos sin bajarlo a valor           |
| Consultivos y accionables                | Teóricos sin aplicación                |
| Seguros y fundamentados                  | Prometedores sin sustento              |

### 9.3 Territorio verbal (palabras de marca)

Crecimiento · Ecosistema · Sistema · Estrategia · Performance · Data · Brandformance · Creatividad · Tecnología · IA · Medios · Optimización · Insights · Conversión · Medición · Escala · Mejora continua.

### 9.4 Lo que evitamos

❌ "Agencia 360" · ❌ "Hacemos de todo" · ❌ "Contenido bonito" · ❌ "Viralizar" como garantía · ❌ "Resultados garantizados" · ❌ "Disruptivo" vacío · ❌ Lenguaje técnico sin bajarlo a negocio.

---

## 10. Especificaciones técnicas para generar PPTX

Estas son las decisiones de implementación para crear un deck Qudox en código (pptxgenjs, python-pptx, etc).

### 10.1 Dimensiones

- Slide widescreen 16:9: **13.333" × 7.5"** (1920×1080 a 144dpi).

### 10.2 Tipografías

Las fuentes a referenciar por nombre en el archivo `.pptx`:

```
"Newsreader SemiBold"   → titulares display (siempre italic = true)
"Manrope"               → todo lo demás
```

PowerPoint las renderizará si están instaladas en la máquina del usuario. Newsreader y Manrope son gratuitas en Google Fonts; el usuario las debe instalar localmente para ver el deck correctamente.

### 10.3 Paleta hex de referencia rápida

```
qx-green        #16B87A
qx-green-bright #38E08C
qx-dark         #0D1512
qx-dark-deep    #06241B
qx-white        #FFFFFF
qx-ink          #1F2937
qx-ink-muted    #5D6B63
```

### 10.4 Márgenes y safe area

- Margen de cada lado: **0.5"** mínimo.
- Banda de footer de patrón ocupa los últimos **0.7–1.0"** verticales del slide.

### 10.5 Espaciado entre elementos

- Header → contenido: 0.5"
- Entre columnas: 0.35"
- Entre bloques de contenido: 0.3"

---

## 11. Do's & Don'ts (consolidado para Claude)

### ✅ DO

- Empezar siempre con `cover` → `toc` → `section-divider` → `content`.
- Cada sección abre con un section-divider numerado en verde brillante.
- Newsreader **siempre italic** y **siempre semibold** para titulares display.
- Manrope sostiene el 80%+ del texto de cada slide.
- Verde es el color institucional de presentaciones — no cyan, no yellow.
- Footer con banda de patrón verde en todo slide claro de contenido.
- Eyebrow en mayúsculas con tracking amplio sobre cada título.
- Callouts con borde izquierdo verde grueso para resaltar implicaciones / conclusiones.
- Cierre conectado a crecimiento con frase corta y contundente.

### ❌ DON'T

- **No** usar cyan `#00FFEF` ni yellow `#EAFF00` puro como color principal del deck (son del producto digital, no de presentaciones).
- **No** usar Newsreader sin italic.
- **No** usar Calibri, Aptos, Arial decorativa ni ninguna fuente fuera de Newsreader + Manrope.
- **No** saturar slides con patrón (footer sí, fondo completo no).
- **No** poner párrafos largos (>6 líneas) — partir en otro slide.
- **No** crear slides 100% texto — siempre hay imagen, dato visual, gráfico o composición.
- **No** centrar párrafos de body — solo títulos.
- **No** usar líneas decorativas debajo de cada título salvo en headers de content (donde sí va una fina línea verde).
- **No** mezclar la paleta de presentaciones con la digital cyan/yellow en el mismo deck.
- **No** convertir `QX Growth System` en marca pública o tratarla como un logo.

---

## 12. Checklist antes de entregar un deck

- [ ] ¿La portada usa Newsreader Italic grande + textura verde + logo QUDOX?
- [ ] ¿Hay un TOC limpio con números verdes Newsreader Italic?
- [ ] ¿Cada sección comienza con un section-divider numerado?
- [ ] ¿Todos los content slides claros tienen banda de patrón verde en el footer?
- [ ] ¿Cada title usa Newsreader Italic y cada body usa Manrope?
- [ ] ¿El cierre conecta con crecimiento y usa Newsreader Italic centrado sobre dark?
- [ ] ¿Hay ritmo entre slides claras y oscuras (no monotonía)?
- [ ] ¿Cero uso de cyan/yellow puro? ¿Cero fuentes fuera del sistema?
- [ ] ¿El logo QUDOX está en cada slide (excepto separadores si así se decide)?
- [ ] ¿Cada slide pasa el filtro "una idea fuerte, lectura clara"?

---

## 13. Fuente y mantenimiento

**Fuente de verdad:** Qudox Brandbook & Presentation System + decks de referencia *MOTOCITY — Fase 2 (Believe It)* y *Katana — Benchmark Línea Gráfica*.
**Última sincronización:** 2026-06-18.

Si vas a producir un deck para Qudox o uno de sus clientes y algo no está cubierto aquí, **pedí confirmación antes de inventar**. Mantener consistencia con los decks de referencia es prioridad.
