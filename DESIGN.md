# DESIGN.md — Qudox

> Sistema de diseño de Qudox para uso por agentes de IA (Claude Code, Cursor, Copilot, v0, etc.) y desarrolladores. Este archivo es la fuente de verdad para colores, tipografía, componentes y estilo de marca. Si algo no está aquí, no se inventa: se consulta el Brandbook completo.

---

## 1. Identidad de marca

**Nombre:** Qudox
**Descriptor oficial:** Growth Marketing Company
**Posicionamiento:** Growth Marketing Company **AI First** con visión regional (Centroamérica y Latinoamérica).
**Tagline / cierre narrativo:** *Together, We Power Growth.* (ES: *Juntos potenciamos el crecimiento.*)

**Qué construye Qudox:** ecosistemas de crecimiento integrados que conectan estrategia, creatividad, data, medios, tecnología, IA y operación bajo una misma visión.

**Marca principal y arquitectura:**
- `Qudox` — marca principal (estratégica, corporativa, metodológica).
- `QX Growth System` — **narrativa interna de metodología**, NO es una marca pública, NO se usa como logo independiente, NO reemplaza a Qudox.
- Submarcas especializadas (todas firman *by Qudox*):
  - **Hype** — influencers.
  - **Blink** — videos cortos.
  - **State of Digital** — investigación y eventos.

---

## 2. Principios de diseño

Estos principios guían cualquier decisión visual y de producto:

1. **Claridad antes que complejidad.**
2. **Estrategia antes que decoración.**
3. **Evidencia antes que promesa vacía.**
4. **Creatividad con propósito.**
5. **Tecnología aplicada, no presumida.**
6. **Cercanía profesional.**
7. **Mensajes accionables y medibles.**

Personalidad de marca: **estratégica, tecnológica, corporativa, creativa, consultiva, clara, dinámica, confiable**.

---

## 3. Sistema de color

### 3.1 Paleta base

| Token            | HEX        | RGB                  | CMYK             | Rol                                                      |
| ---------------- | ---------- | -------------------- | ---------------- | -------------------------------------------------------- |
| `color-dark`     | `#070A0B`  | `7, 10, 11`          | `36, 9, 0, 96`   | Base de profundidad. Fondo principal del sistema.        |
| `color-white`    | `#FFFFFF`  | `255, 255, 255`      | `0, 0, 0, 0`     | Espacio de lectura. Fondo claro.                         |
| `color-cyan`     | `#00FFEF`  | `0, 255, 239`        | `60, 0, 22, 0`   | **Acento principal**. Foco, energía tecnológica.         |
| `color-yellow`   | `#EAFF00`  | `234, 255, 0`        | `8, 0, 100, 0`   | Acento de energía. Segundo acento, énfasis puntuales.    |
| `color-green`    | `#16B87A`  | `22, 184, 122`       | `88, 0, 34, 28`  | Resalte terciario. **SOLO presentaciones**, sobre dark.  |

### 3.2 Reglas de uso del color

- **Dark + White sostienen ~75%** del sistema (50% dark + 25% white). Estructura y lectura.
- **Cyan ~15%** — acento principal para foco y énfasis.
- **Yellow + degradado ~10%** — gestos de mayor energía.
- ❌ **Cyan y Yellow NUNCA se usan como fondo sólido de página.** Solo como acento sobre dark, blanco o textura.
- ❌ **Green nunca va sobre blanco**, no es fondo, no reemplaza cyan ni yellow. Reservado a resaltes de datos en slides sobre fondo dark.
- ✅ Contraste alto siempre. Si el contraste no permite leer, hay que cambiar el fondo.

### 3.3 Degradado de marca

Va de `cyan → yellow` en sentido **lineal o diagonal**. Es el gesto más expresivo del sistema.

- ✅ Usar en superficies, separadores y líneas.
- ❌ **Nunca** sobre texto.
- ❌ **Nunca** como relleno del logo.

```css
background: linear-gradient(135deg, #00FFEF 0%, #EAFF00 100%);
```

### 3.4 Tokens CSS

```css
:root {
  /* Base */
  --color-dark: #070A0B;
  --color-white: #FFFFFF;

  /* Acentos */
  --color-cyan: #00FFEF;
  --color-yellow: #EAFF00;
  --color-green: #16B87A; /* solo presentaciones */

  /* Degradado */
  --gradient-brand: linear-gradient(135deg, #00FFEF 0%, #EAFF00 100%);

  /* Semánticos (UI digital — extrapolado para producto) */
  --bg-default: var(--color-dark);
  --bg-surface: #0E1314;          /* dark un paso más arriba */
  --bg-elevated: #161B1D;
  --bg-inverse: var(--color-white);

  --text-primary: var(--color-white);
  --text-secondary: rgba(255, 255, 255, 0.72);
  --text-muted: rgba(255, 255, 255, 0.56);
  --text-on-light: var(--color-dark);

  --accent-primary: var(--color-cyan);
  --accent-secondary: var(--color-yellow);
  --accent-success: var(--color-green);

  --border-subtle: rgba(255, 255, 255, 0.08);
  --border-default: rgba(255, 255, 255, 0.16);
  --border-strong: rgba(255, 255, 255, 0.32);
}
```

### 3.5 Tailwind config

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        qx: {
          dark:   '#070A0B',
          white:  '#FFFFFF',
          cyan:   '#00FFEF',
          yellow: '#EAFF00',
          green:  '#16B87A',
        },
      },
      backgroundImage: {
        'qx-gradient': 'linear-gradient(135deg, #00FFEF 0%, #EAFF00 100%)',
      },
    },
  },
};
```

---

## 4. Tipografía

### 4.1 Familias

| Token              | Familia          | Uso                                                                 |
| ------------------ | ---------------- | ------------------------------------------------------------------- |
| `font-display`     | **Empower Serif** | Titulares, frases de impacto, énfasis editoriales, momentos de marca. |
| `font-body`        | **Manrope**       | Cuerpo, subtítulos, etiquetas, bullets, tablas, captions, UI.       |

**Pesos disponibles:**
- Empower Serif: `Regular`, `Italic`.
- Manrope: `Semibold (600)`, `Bold (700)`, `Extra Bold (800)`. *(Regular y Medium se usan en cuerpos; añadirlos al cargar la fuente.)*

### 4.2 Jerarquía de texto

| Rol                  | Familia          | Peso / estilo                                  |
| -------------------- | ---------------- | ---------------------------------------------- |
| Título principal     | Empower Serif    | Regular o Italic según énfasis                 |
| Frase de impacto     | Empower Serif    | Regular / Italic                               |
| Subtítulo            | Manrope          | Bold (700) o Semibold (600)                    |
| Cuerpo               | Manrope          | Regular o Medium                               |
| Etiqueta / overline  | Manrope          | Semibold en MAYÚSCULAS o small caps           |
| Dato destacado       | Manrope          | Extra Bold (800)                               |

### 4.3 Reglas de combinación

- Empower Serif aporta **carácter**; Manrope sostiene **lectura, estructura y precisión**.
- Patrones válidos: título serif + cuerpo sans / palabra serif dentro de frase sans / dato sans con énfasis serif.
- ❌ No usar tipografías externas sin criterio.

### 4.4 Tokens CSS

```css
:root {
  --font-display: 'Empower Serif', 'Times New Roman', serif;
  --font-body: 'Manrope', system-ui, -apple-system, 'Segoe UI', sans-serif;

  /* Pesos */
  --fw-regular: 400;
  --fw-medium: 500;
  --fw-semibold: 600;
  --fw-bold: 700;
  --fw-extrabold: 800;

  /* Escala (extrapolación digital base 16px) */
  --fs-xs: 0.75rem;     /* 12 */
  --fs-sm: 0.875rem;    /* 14 */
  --fs-base: 1rem;      /* 16 */
  --fs-lg: 1.125rem;    /* 18 */
  --fs-xl: 1.5rem;      /* 24 */
  --fs-2xl: 2rem;       /* 32 */
  --fs-3xl: 2.5rem;     /* 40 */
  --fs-4xl: 3.5rem;     /* 56 */
  --fs-5xl: 4.5rem;     /* 72 */

  /* Line-heights */
  --lh-tight: 1.05;     /* títulos serif */
  --lh-snug: 1.2;       /* subtítulos */
  --lh-normal: 1.5;     /* cuerpo */
  --lh-relaxed: 1.65;   /* lectura larga */

  /* Tracking */
  --ls-tight: -0.02em;  /* títulos serif grandes */
  --ls-normal: 0;
  --ls-wide: 0.08em;    /* etiquetas en mayúsculas */
}
```

### 4.5 Tailwind config

```js
theme: {
  extend: {
    fontFamily: {
      display: ['"Empower Serif"', 'serif'],
      body:    ['Manrope', 'system-ui', 'sans-serif'],
    },
  },
}
```

---

## 5. Espaciado, radios y elevación

> *Extrapolado para producto digital. El brandbook se enfoca en print/presentaciones; estas escalas mantienen el carácter del sistema (sobrio, alto contraste, geométrico).*

### 5.1 Escala de espaciado (base 4px)

```css
:root {
  --space-0: 0;
  --space-1: 0.25rem;   /*  4 */
  --space-2: 0.5rem;    /*  8 */
  --space-3: 0.75rem;   /* 12 */
  --space-4: 1rem;      /* 16 */
  --space-5: 1.5rem;    /* 24 */
  --space-6: 2rem;      /* 32 */
  --space-7: 3rem;      /* 48 */
  --space-8: 4rem;      /* 64 */
  --space-9: 6rem;      /* 96 */
  --space-10: 8rem;     /* 128 */
}
```

### 5.2 Radios

Geometría limpia, derivada del símbolo Q (círculo perfecto). Radios suaves, nunca exagerados.

```css
:root {
  --radius-none: 0;
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 20px;
  --radius-pill: 9999px;   /* botones tipo pill — alineado al carácter del símbolo Q */
}
```

### 5.3 Sombras

Sutiles. La marca trabaja con contraste de color y profundidad oscura, no con sombras dramáticas.

```css
:root {
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.32);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.40);
  --shadow-lg: 0 12px 32px rgba(0, 0, 0, 0.48);
  --shadow-glow-cyan: 0 0 24px rgba(0, 255, 239, 0.32);
  --shadow-glow-yellow: 0 0 24px rgba(234, 255, 0, 0.24);
}
```

❌ Nunca aplicar sombras al logo.

---

## 6. Logo y símbolo Q

### 6.1 Versiones oficiales

| Versión                          | Cuándo usar                                              |
| -------------------------------- | -------------------------------------------------------- |
| Horizontal con descriptor        | **Firma primaria.** Default en la mayoría de aplicaciones. |
| Vertical con descriptor          | Formatos compactos o cuadrados.                          |
| Sin descriptor                   | Marca ya reconocida en contexto.                         |
| Ícono Q (isotipo / avatar)       | Avatares, favicons, espacios mínimos.                    |

### 6.2 Construcción (módulo X = altura del símbolo Q)

- Horizontal con descriptor → proporción `7.8X · 1X`, divisor `0.5X`.
- Sin descriptor → proporción `5.65X · 1X`.
- Vertical con descriptor → proporción `3.9X · 1X`, centrado sobre eje del símbolo.
- Ícono Q → círculo base, proporción `1 : 1.18` (no se redibuja, no se rota, no se altera el grosor).

### 6.3 Área de respeto

Mínimo equivalente a una `X` (altura del símbolo Q) en los **cuatro lados**. Ningún elemento gráfico, texto o borde puede invadirla.

### 6.4 Tamaños mínimos

| Aplicación | Tamaño mínimo |
| ---------- | ------------- |
| Desktop    | 240 px        |
| Mobile     | 140 px        |
| Avatar     | Solo Q        |
| Favicon    | 16 px (solo Q) |

### 6.5 Versiones de color

- **Positiva** sobre fondos claros.
- **Negativa** sobre fondos oscuros.
- Permitido sobre: blanco, dark, textura cyan, textura oscura.

### 6.6 Usos incorrectos (no hacer)

❌ No deformar · ❌ No rotar · ❌ No usar con bajo contraste · ❌ No recolorear · ❌ No aplicar sombras · ❌ No usar sobre fondo sin contraste suficiente.

---

## 7. Fondos y patrón

### 7.1 Sistema de fondos (3 estilos)

1. **Profundidad oscura** — portadas y separadores institucionales.
2. **Energía cyan** — piezas de alto impacto.
3. **Atmósfera de marca** — portadas institucionales con textura líquida.

Reglas: se aplican siempre a sangre completa y limpios. **Sin** filtros, sombras ni capas adicionales encima.

### 7.2 El patrón Qudox

Recurso gráfico derivado de la Q: combina círculos, flechas y chevrons con textura líquida.

**Versiones:**
- Texturizado sobre blanco.
- Blanco sobre negro.

**DO ✅**
- Texturizado sobre fondo blanco.
- Blanco sobre fondo negro.
- Como recurso de portada o separador.
- Como borde, marco o detalle de composición.
- A sangre completa, sin recortes forzados.

**DON'T ❌**
- Detrás de textos largos.
- Cuando reduce contraste o lectura.
- Sobre fondos de color sólido.
- Recoloreado fuera del sistema.
- Compitiendo con el logo o la Q.
- Sobre data compleja o documentos legales muy formales.

---

## 8. Componentes UI (lineamientos)

> Extrapolado del lenguaje visual del Brandbook para producto digital. Los componentes deben sentirse **estratégicos, tecnológicos y corporativos** — sobrios, de alto contraste, sin saturación.

### 8.1 Botones

| Variante      | Fondo                | Texto              | Borde                     | Uso                                          |
| ------------- | -------------------- | ------------------ | ------------------------- | -------------------------------------------- |
| Primary       | `--color-cyan`       | `--color-dark`     | ninguno                   | Acción principal. Una por vista.             |
| Secondary     | transparente         | `--color-white`    | `1px solid --border-strong` | Acción secundaria sobre fondos oscuros.    |
| Tertiary      | transparente         | `--color-cyan`     | ninguno                   | Enlaces y acciones de soporte.               |
| Destructive   | `#FF4D4D` *(definir)* | `--color-white`    | ninguno                   | Acciones destructivas (no en brandbook).     |

- Tipografía: `Manrope Semibold (600)` o `Bold (700)`.
- Radio recomendado: `--radius-pill` o `--radius-md`.
- Padding: `var(--space-3) var(--space-5)` (default).
- ❌ Yellow no se usa como fondo de botón principal (es acento de energía puntual, no acción).

### 8.2 Tarjetas / superficies

- Fondo: `--bg-surface` o `--bg-elevated`.
- Borde: `--border-subtle`.
- Radio: `--radius-lg`.
- Padding interno: `var(--space-5)` o `var(--space-6)`.
- Dato destacado o KPI dentro de la tarjeta: `Manrope Extra Bold`, color `--color-cyan` para resalte principal.

### 8.3 Inputs / formularios

- Fondo: `--bg-elevated` sobre dark, o `--color-white` sobre claro.
- Borde: `--border-default`, foco: `--color-cyan` con `--shadow-glow-cyan`.
- Tipografía: `Manrope Regular`.
- Labels: `Manrope Semibold` en MAYÚSCULAS (con `letter-spacing: --ls-wide`).

### 8.4 Tablas y data

- Headers: `Manrope Semibold` en mayúsculas.
- Filas: `Manrope Regular`, line-height `--lh-normal`.
- KPIs principales: `Manrope Extra Bold`, en `--color-cyan` cuando son el dato protagonista.
- **No saturar tablas.** Si hay >5 columnas críticas, replantear como tarjetas de métrica.

### 8.5 Slides de presentación (referencia)

Tipos del sistema: `Portada`, `Separador`, `Frase de impacto`, `Contexto`, `Reto`, `Insight`, `Data`, `Metodología`, `Ecosistema`, `Roadmap`, `Entregables`, `Caso de éxito`, `Cierre`.

Principios de slide:
1. Una idea fuerte por slide.
2. Títulos claros y contundentes.
3. Textos cortos, sin párrafos extensos.
4. Data visual antes que data saturada (3–5 datos clave máx.).
5. Uso intencional del patrón.
6. Contraste alto.
7. Ritmo entre slides oscuras, claras y visuales.
8. Cierre siempre conectado a crecimiento.

---

## 9. Identidad verbal (microcopy y contenido)

### 9.1 Tono

> *Qudox habla con claridad estratégica, seguridad corporativa, sensibilidad creativa y visión tecnológica.*

Proyecta experiencia, pensamiento estructurado y capacidad de ejecución, sin sonar rígido, exagerado o artificial.

### 9.2 Sí somos / No somos

| ✅ Sí somos                          | ❌ No somos                              |
| ------------------------------------ | ---------------------------------------- |
| Estratégicos y orientados a negocio  | Genéricos o decorativos                  |
| Claros y estructurados               | Confusos o improvisados                  |
| Creativos con propósito              | Creativos solo por estética              |
| Tecnológicos y AI First              | Técnicos sin bajarlo a valor             |
| Consultivos y accionables            | Teóricos sin aplicación                  |
| Cercanos con criterio profesional    | Excesivamente informales                 |
| Seguros y fundamentados              | Prometedores sin sustento                |
| Dinámicos y adaptables               | Rígidos o desconectados del cambio       |

### 9.3 Territorio verbal (vocabulario de marca)

`Crecimiento` · `Ecosistema` · `Sistema` · `Estrategia` · `Performance` · `Data` · `Brandformance` · `Creatividad` · `Contenido` · `Tecnología` · `IA` · `Medios` · `Optimización` · `Comunidad` · `Audiencias` · `Insights` · `Conversión` · `Medición` · `Escala` · `Mejora continua`.

### 9.4 Lo que evitamos

❌ "Agencia 360" como definición principal.
❌ "Hacemos de todo" sin enfoque.
❌ "Contenido bonito" como promesa.
❌ "Viralizar" como garantía.
❌ "Resultados garantizados" sin fundamento.
❌ "Disruptivo" usado de forma vacía.
❌ Lenguaje excesivamente técnico sin bajarlo a negocio.

### 9.5 Elevator pitches

**15 seg.** — Qudox es una Growth Marketing Company AI First que construye ecosistemas de crecimiento integrando estrategia, creatividad, data, medios y tecnología para ayudar a las marcas a crecer con mayor consistencia.

**30 seg.** — En Qudox ayudamos a las marcas a dejar de depender de acciones aisladas y comenzar a operar bajo ecosistemas de crecimiento. Conectamos estrategia, creatividad, contenido, medios, data, tecnología e inteligencia artificial para construir resultados medibles, sostenibles y escalables.

---

## 10. Aplicaciones (dónde vive Qudox)

Presentaciones · Propuestas comerciales · Documentos internos · Redes sociales · Eventos · Reportes · Merch · Firmas de correo · Sitio web · Casos de éxito · Comunicación interna · Todo el ecosistema digital.

---

## 11. Do's & Don'ts (consolidado)

### ✅ DO

- Usar el logo con suficiente contraste.
- Respetar el área de seguridad del logo.
- Aplicar la paleta con intención (75% dark+white, 15% cyan, 10% yellow+gradient).
- Usar Empower Serif para momentos de marca.
- Usar Manrope para claridad y lectura.
- Mantener pantallas limpias y jerárquicas.
- Usar la Q como recurso propietario.
- Conectar siempre la comunicación con crecimiento.
- Usar cyan para resaltar el dato protagonista.

### ❌ DON'T

- Saturar piezas con patrón o textura.
- Usar fondos que dificulten la lectura.
- Cambiar colores del logo.
- Deformar la Q.
- Usar tipografías externas sin criterio.
- Convertir `QX Growth System` en marca pública.
- Presentar servicios como acciones sueltas.
- Comunicar sin conectar a estrategia o resultado.
- Usar cyan o yellow como fondo sólido de página.
- Aplicar el degradado sobre texto o como relleno del logo.

---

## 12. Checklist antes de publicar

- [ ] ¿La pieza se siente estratégica, tecnológica, corporativa y creativa?
- [ ] ¿El logo está bien aplicado (versión, contraste, área de respeto, tamaño mínimo)?
- [ ] ¿La Q se usa correctamente (sin deformar, rotar ni recolorear)?
- [ ] ¿El color tiene contraste suficiente?
- [ ] ¿La tipografía respeta la jerarquía (Empower Serif en titulares, Manrope en cuerpo)?
- [ ] ¿El patrón suma sin saturar?
- [ ] ¿El mensaje suena a Qudox (claro, estratégico, accionable)?
- [ ] ¿La comunicación conecta con crecimiento?
- [ ] ¿La pieza podría pertenecer claramente al ecosistema Qudox?

---

## 13. Fuente y mantenimiento

**Fuente de verdad:** Qudox Brandbook & Presentation System (Figma, archivo `QX-Brandbook`).
**Última sincronización:** 2026-06-16.
**Notas para agentes de IA:**
- Si el agente necesita un valor de color, tipografía o componente que **no está aquí**, debe pedir confirmación o consultar el Brandbook antes de inventarlo.
- Los tokens de espaciado, radios, sombras y componentes UI son **extrapolaciones digitales** consistentes con el lenguaje visual del Brandbook; el Brandbook original se enfoca en print y presentaciones.
- Cualquier nuevo componente debe pasar el checklist de la sección 12 antes de considerarse oficial.
