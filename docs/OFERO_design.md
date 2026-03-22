# OFERO — Guía de Diseño para Desarrollo de Aplicativos

Documento extraído de la Guía de Marca Corporativa OFERO (Septiembre 2024).
Usar como referencia obligatoria para cualquier desarrollo de interfaz visual.

---

## 1. IDENTIDAD DE MARCA

**Nombre:** OFERO  
**Sector:** Bicicletas y motocicletas eléctricas de alta calidad  
**Fundada:** 2022  
**Valores de marca:** Libertad · Originalidad · Estilo · Fiabilidad · Eléctrica · Óptimo  
**Concepto:** Far / Freedom / Fashion — Movilidad sostenible, autonomía y confianza.

---

## 2. LOGOTIPO

### Componentes
- **Logotipo (A):** Componente verbal/tipográfico con el nombre "ofero" y slogan.
- **Identificador (B):** Componente gráfico — la letra **F** estilizada dentro de un círculo. Puede usarse de forma independiente para representar la marca.

### Versiones permitidas
| Versión | Uso |
|---|---|
| Full color sobre fondo blanco | Uso general digital e impreso |
| Negativo (blanco sobre negro) | Fondos oscuros corporativos |
| Monocromático negro | Impresiones offset, sellos |
| Sobre fondo verde corporativo | Material POP, señalética |
| Con degradado | Exclusivo para uso web y pantallas |
| Identificador solo (F) | Cuando el espacio no permite el logo completo |

### Versiones NO permitidas
- ❌ Rotar el identificador
- ❌ Cambiar fuentes corporativas
- ❌ Deformar proporciones
- ❌ Invertir el orden de elementos
- ❌ Usar sobre fondos de colores no corporativos
- ❌ Cambiar los colores determinados

### Área de protección
El logotipo debe tener un área libre de otros elementos equivalente al **20% de su ancho** en cada lado.

### Dimensiones mínimas
| Versión | Tamaño mínimo |
|---|---|
| Logo completo | 2.5 cm de ancho |
| Logo completo preferido | 6 cm de ancho |
| Por debajo del mínimo | Usar solo el identificador (F) |

---

## 3. TIPOGRAFÍA CORPORATIVA

**Familia tipográfica única: [Manrope](https://fonts.google.com/specimen/Manrope)** — Uso comercial gratuito, disponible en Google Fonts.

| Peso | Uso |
|---|---|
| **Manrope ExtraBold** | Títulos principales, nombre de marca |
| **Manrope SemiBold** | Subtítulos, textos complementarios |
| **Manrope Regular** | Cuerpo de texto, párrafos |

> El resto de la familia Manrope (Light, Medium, Bold) puede usarse en textos de soporte.

### Implementación CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;800&display=swap');

font-family: 'Manrope', sans-serif;
font-weight: 800; /* ExtraBold — Títulos */
font-weight: 600; /* SemiBold — Subtítulos */
font-weight: 400; /* Regular — Cuerpo */
```

---

## 4. COLORES CORPORATIVOS

### Colores Principales

| Nombre | HEX | RGB | CMYK | Pantone | Uso |
|---|---|---|---|---|---|
| **Verde OFERO** | `#70D84A` | R112 G216 B74 | C52 M0 Y82 K0 | 7488 | Color primario. Innovación, sostenibilidad, energía limpia. Títulos, CTAs, detalles, acentos. |
| **Negro OFERO** | `#1D1E21` | R29 G30 B33 | C79 M69 Y58 K78 | 1559 | Color base. Elegancia, profesionalismo, tecnología. Fondos, textos principales. |

### Colores Auxiliares

| Nombre | HEX | RGB | CMYK | Pantone | Uso |
|---|---|---|---|---|---|
| **Verde Lima** | `#C5E21B` | R197 G226 B27 | C29 M0 Y80 K0 | 2297C | Energía, dinamismo. Acentos secundarios, highlights. |
| **Gris Oscuro** | `#63666A` | R99 G102 B106 | C40 M30 Y20 K55 | Cool Gray 10C | Equilibrio, neutralidad. Textos secundarios, bordes. |
| **Gris Claro** | `#E8EAEA` | R232 G234 B234 | C11 M6 Y8 K0 | 1543 | Suavidad, claridad. Fondos de sección, separadores. |

### Tonos adicionales identificados

```
#47494E — Gris medio oscuro
#26282D — Gris muy oscuro (casi negro)
#030303 — Negro absoluto
#C4DA4B — Verde lima variación
#87CF5E — Verde medio (entre primario y lima)
```

### Degradados (exclusivo web/digital)

Degradados aplicando la paleta de marca para aportar dinamismo:

```css
/* Degradado verde principal */
background: linear-gradient(135deg, #70D84A, #C5E21B);

/* Degradado oscuro corporativo */
background: linear-gradient(135deg, #1D1E21, #26282D);

/* Degradado verde a negro */
background: linear-gradient(135deg, #70D84A, #1D1E21);

/* Degradado verde lima */
background: linear-gradient(135deg, #C5E21B, #87CF5E);
```

### Variables CSS recomendadas

```css
:root {
  /* Colores principales */
  --ofero-green: #70D84A;
  --ofero-black: #1D1E21;

  /* Colores auxiliares */
  --ofero-lime: #C5E21B;
  --ofero-gray-dark: #63666A;
  --ofero-gray-light: #E8EAEA;

  /* Tonos adicionales */
  --ofero-gray-mid: #47494E;
  --ofero-gray-deeper: #26282D;
  --ofero-black-pure: #030303;
  --ofero-green-mid: #87CF5E;
  --ofero-lime-alt: #C4DA4B;

  /* Tipografía */
  --font-family: 'Manrope', sans-serif;
  --font-title: 800;
  --font-subtitle: 600;
  --font-body: 400;
}
```

---

## 5. PRINCIPIOS DE APLICACIÓN VISUAL

### Combinaciones recomendadas

| Fondo | Texto / Logo | Acento |
|---|---|---|
| Negro `#1D1E21` | Blanco + Verde `#70D84A` | Verde Lima `#C5E21B` |
| Verde `#70D84A` | Negro `#1D1E21` + Blanco | Gris claro `#E8EAEA` |
| Blanco / Gris claro | Negro `#1D1E21` | Verde `#70D84A` |
| Gris oscuro `#63666A` | Blanco + Verde | Verde Lima |

### Reglas de contraste y armonía
- Buscar siempre **armonía y contraste correcto** para evitar saturación entre negro y verde.
- Los colores fuertes (negro y verde) deben balancearse con grises y blancos.
- El verde debe usarse como **acento o elemento destacado**, no como fondo dominante en interfaces extensas.
- Mantener imagen **moderna y minimalista**.

---

## 6. GRÁFICOS AUXILIARES

La marca dispone de tres tipos de elementos gráficos de soporte (no reemplazan al logo):

1. **Auxiliar 1 — Forma de hoja:** Patrón matricial que expresa protección ambiental y tecnología. El ancho y densidad pueden ajustarse según la aplicación.
2. **Auxiliar 2 — Forma de bandera:** Unidad gráfica para expresar moda y tecnología.
3. **Auxiliar 3 — Imagen dividida del logo:** Fragmento del logotipo que se asemeja a un vehículo eléctrico. Se aplica como subrayado decorativo. El contraste con el fondo no debe ser excesivo.

> Estos gráficos son decorativos y de soporte. **No deben interferir con el logotipo ni los elementos centrales de comunicación.**

---

## 7. APLICACIÓN EN INTERFACES DIGITALES

### Jerarquía visual recomendada
```
TÍTULO PRINCIPAL     → Manrope ExtraBold · Verde #70D84A o Blanco · Tamaño grande
Subtítulo            → Manrope SemiBold · Gris claro o Negro · Tamaño medio
Cuerpo de texto      → Manrope Regular · Gris claro #E8EAEA o Negro #1D1E21
CTA / Botones        → Manrope SemiBold o ExtraBold · Fondo verde · Texto negro
Etiquetas / Chips    → Manrope SemiBold · Borde verde · Fondo oscuro
```

### Estilo general de UI
- **Tema preferido:** Oscuro con acentos verdes (fondo `#1D1E21`, acentos `#70D84A`)
- **Bordes:** Sutiles, en grises oscuros o con acento verde para elementos activos
- **Sombras:** Oscuras con leve tinte verde para profundidad
- **Íconos:** Lineales o minimalistas, en verde o blanco
- **Botones primarios:** Fondo `#70D84A`, texto `#1D1E21`, Manrope SemiBold/ExtraBold
- **Botones secundarios:** Borde `#70D84A`, texto `#70D84A`, fondo transparente

---

## 8. RESUMEN RÁPIDO PARA DESARROLLO

```
Fuente:        Manrope (Google Fonts) — 400 / 600 / 800
Color primario: #70D84A (verde)
Color base:     #1D1E21 (negro)
Acento 2:       #C5E21B (verde lima)
Neutros:        #63666A / #E8EAEA
Tema UI:        Oscuro con acentos verdes
Degradados:     Permitidos solo en digital
Logo mínimo:    2.5cm / No distorsionar / No recolorear
Identificador:  "F" en círculo — uso independiente permitido
```
