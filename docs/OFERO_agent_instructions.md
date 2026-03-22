# INSTRUCCIONES PARA AGENTE DE IA
## Proyecto: OFERO Store Locator — Aplicativo Web

---

## ROL DEL AGENTE

Eres un desarrollador frontend senior especializado en interfaces web modernas, con experiencia en diseño de sistemas de identidad visual y aplicaciones de usuario final. Tu misión es construir un aplicativo web completo, funcional y visualmente impecable que respete al 100% la guía de marca de OFERO. El resultado debe ser un archivo HTML único, autocontenido, listo para publicar, que no requiera dependencias externas más allá de Google Fonts.

---

## OBJETIVO DEL APLICATIVO

Construir una **página web de localización de tiendas OFERO** que permita al usuario encontrar la sede más cercana a su ubicación mediante un sistema de filtros en cascada:

```
Seleccionar Departamento → Seleccionar Ciudad → Seleccionar Tienda → Ver Información
```

El resultado final debe mostrar la información de la tienda seleccionada en formato **card** con todos los datos de contacto y ubicación.

---

## IDENTIDAD VISUAL — GUÍA DE MARCA OFERO

### Tipografía
- **Fuente única:** `Manrope` — importar desde Google Fonts
- `font-weight: 800` → Títulos principales (ExtraBold)
- `font-weight: 600` → Subtítulos y etiquetas (SemiBold)
- `font-weight: 400` → Cuerpo de texto (Regular)

```html
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;800&display=swap" rel="stylesheet">
```

### Paleta de Colores

```css
:root {
  /* Principales */
  --ofero-green:      #70D84A;   /* Verde vibrante — acento principal, CTAs, highlights */
  --ofero-black:      #1D1E21;   /* Negro corporativo — fondo base, textos sobre fondo claro */

  /* Auxiliares */
  --ofero-lime:       #C5E21B;   /* Verde lima — acentos secundarios, hover states */
  --ofero-gray-dark:  #63666A;   /* Gris oscuro — textos secundarios, bordes sutiles */
  --ofero-gray-light: #E8EAEA;   /* Gris claro — fondos de sección, fondos de cards */

  /* Tonos adicionales */
  --ofero-gray-mid:   #47494E;
  --ofero-gray-deep:  #26282D;
  --ofero-black-pure: #030303;
  --ofero-green-mid:  #87CF5E;

  /* Tipografía */
  --font: 'Manrope', sans-serif;
  --fw-title:    800;
  --fw-subtitle: 600;
  --fw-body:     400;
}
```

### Estilo visual general
- **Tema:** Oscuro. Fondo principal `#1D1E21`, secciones internas en `#26282D` o `#47494E`.
- **Acentos:** Verde `#70D84A` para elementos activos, CTAs, bordes de foco, iconos.
- **Cards:** Fondo `#26282D`, borde izquierdo o superior en verde `#70D84A`, esquinas redondeadas (`border-radius: 12px`).
- **Botones primarios:** Fondo `#70D84A`, texto `#1D1E21`, `font-weight: 800`.
- **Selects/Dropdowns:** Fondo `#26282D`, borde `#47494E`, texto `#E8EAEA`. Al estar activo/focus: borde `#70D84A`.
- **Degradados permitidos (solo digital):**
  ```css
  linear-gradient(135deg, #70D84A, #C5E21B)  /* Verde vibrante */
  linear-gradient(135deg, #1D1E21, #26282D)   /* Fondo oscuro sutil */
  linear-gradient(135deg, #70D84A, #1D1E21)   /* Verde a negro */
  ```

---

## ESPECIFICACIONES FUNCIONALES

### Flujo de la aplicación

```
1. Usuario abre la app
2. Ve un selector de DEPARTAMENTO (poblado con todos los departamentos disponibles)
3. Al seleccionar departamento → se habilita y puebla el selector de CIUDAD
4. Al seleccionar ciudad → se habilita y puebla el selector de TIENDA
5. Al seleccionar tienda → aparece la CARD con la información completa
6. El usuario puede hacer clic en el teléfono para llamar directamente (tel: link)
```

### Comportamiento de los selects
- Los selectores deben estar **en cascada**: Ciudad deshabilitado hasta que se elija Departamento, Tienda deshabilitada hasta que se elija Ciudad.
- Al cambiar Departamento, reiniciar Ciudad y Tienda.
- Al cambiar Ciudad, reiniciar Tienda y ocultar card.
- Placeholder de cada select:
  - Departamento: `"Selecciona un departamento"`
  - Ciudad: `"Selecciona una ciudad"`
  - Tienda: `"Selecciona una tienda"`

### Card de información
La card debe mostrar:
- **Nombre de la tienda** (prominente, en verde o blanco)
- **Ícono de ubicación** + Dirección completa
- **Ícono de teléfono** + Número como enlace `tel:+57XXXXXXXXXX`
- **Ciudad y Departamento**
- Botón o link secundario: `"¿Cómo llegar?"` que abra Google Maps con la dirección

### Animaciones
- La card debe aparecer con una animación suave de entrada (fade + slide up).
- Los selects deben tener transición suave al habilitarse/deshabilitarse.
- Hover en la card con leve elevación (box-shadow verde sutil).

---

## ESTRUCTURA DEL ARCHIVO

El entregable debe ser **un único archivo `index.html`** que incluya:
- CSS embebido en `<style>` dentro del `<head>`
- JavaScript embebido en `<script>` al final del `<body>`
- Todos los datos de las tiendas como un objeto/array JSON en el JavaScript
- Solo dependencia externa permitida: Google Fonts (via `<link>`)

### Estructura de datos JS sugerida

```javascript
const tiendas = {
  "ANTIOQUIA": {
    "APARTADO": [
      {
        nombre: "Ofero Apartado — Carrera 98",
        direccion: "Carrera 98 # 95 - 25 - Barrio Fundadores",
        telefono: "3215261638",
        telefonoDisplay: "321 5261638"
      }
    ],
    "MEDELLIN": [
      {
        nombre: "Ofero Alpujarra — Calle 44",
        direccion: "Calle 44 # 51-33",
        telefono: "3004200527",
        telefonoDisplay: "300 4200527"
      },
      // ... más tiendas
    ]
  },
  // ... más departamentos
};
```

---

## DATOS DE LAS TIENDAS

A continuación se listan **todas las tiendas** organizadas por Departamento → Ciudad → Sede.
Usar estos datos exactos para poblar el objeto `tiendas` en el JS.

### ANTIOQUIA
**APARTADO:** Ofero Apartado — Carrera 98 | Carrera 98 # 95 - 25 - Barrio Fundadores | 3215261638
**BELLO:** Ofero Bello — Carrera 51 | Carrera 51 # 51-36 - Barrio Pérez | 3045981034
**CAUCASIA:** Ofero Caucasia — Carrera 20 | Carrera 20 Calle 12 - 37 | 3229084514
**ENVIGADO:** Ofero Envigado — Calle 33 | Calle 33B Sur # 42 - 8 | 3046737555
**ITAGÜÍ:** Ofero Itagüí — Carrera 49 | Carrera 49 # 52-04 | 3216687643
**MEDELLÍN:** Ofero Alpujarra — Calle 44 | Calle 44 # 51-33 | 3004200527
**MEDELLÍN:** Ofero Av Colombia La 65 | Carrera 65 # 50-12 | 3022176332
**MEDELLÍN:** Ofero La 33 — Calle 33 | Calle 33 Carrera 65C - 109 | 3019552159
**MEDELLÍN:** Ofero La 70 — Calle 44 | Calle 44 # 71-78 Piso 1 - Las Américas | 3022176120
**MEDELLÍN:** Ofero Poblado — Calle 10 | Calle 10 # 43DD - 5 - Poblado | 3018520137
**RIONEGRO:** Ofero Rionegro — Calle 51 | Calle 51 # 46-45 | 3234684304
**TURBO:** Ofero Turbo — Carrera 14 | Carrera 14 # 100-27 - Barrio Centro | 3145453184
**URABÁ:** Ofero San Pedro de Urabá — Calle 50 | Calle 50 Carrera 45A - 07 | 3218579143

### ARAUCA
**ARAUCA:** Ofero Arauca — Calle 22 | Calle 22 # 19-35 | 3193263325

### ATLÁNTICO
**BARANOA:** Ofero Baranoa — Carrera 19 | Carrera 19 Calle 13C - Barrio Caldas | 3243620132
**BARRANQUILLA:** Ofero Calle 53 | Calle 53 # 46-187 | 3004433085
**BARRANQUILLA:** Ofero Calle 64 | Carrera 21B # 64-10 | 3145577836
**BARRANQUILLA:** Ofero Calle 68 | Carrera 43 # 68-16 | 3023680315
**BARRANQUILLA:** Ofero Calle 72 | Calle 72 # 45-50 Local 10 | 3226562837
**BARRANQUILLA:** Ofero CC Nuestro Atlántico | Av. Murillo # 131A-13-167 | 3114235892
**BARRANQUILLA:** Ofero CC Parque Alegra | CC Parque Alegra | 3233306574
**BARRANQUILLA:** Ofero Centro — Carrera 45B | Carrera 45B # 34-37 Local 8 | 3011379888
**BARRANQUILLA:** Ofero Éxito Murillo | Éxito Murillo, Barranquilla | 3112555060
**BARRANQUILLA:** Ofero JM — Calle 34 | Calle 34 Carrera 45C - Local 01 - CC Portal de la 34 | 3002230203
**BARRANQUILLA:** Ofero La 21 — Calle 47 | Calle 47 # 20-170 | 3012758267
**BARRANQUILLA:** Ofero La 46 — Carrera 46 | Carrera 46 # 82-241 | 3003252596
**BARRANQUILLA:** Ofero La 75 — Calle 75 | Calle 75 # 44-73 Esquina | 3122076194
**BARRANQUILLA:** Ofero La 8 — Carrera 8 | Carrera 8 # 44-12 | 3046229486
**BARRANQUILLA:** Ofero La Ciudadela — Calle 46 | Calle 46 # 1Sur-08 - Ciudadela 20 de Julio | 3001666004
**BARRANQUILLA:** Ofero La Paz — Carrera 13 | Carrera 13 Calle 109A Esquina - Barrio La Paz | 3137756837
**BARRANQUILLA:** Ofero La Pradera — Calle 110 | Calle 110 # 34-137 - Eds. Primax La Pradera | 3205926816
**BARRANQUILLA:** Ofero Metropolitano | Éxito Metropolitano Barranquilla | 3135829104
**BARRANQUILLA:** Ofero Paseo Bolívar 38 — Calle 34 | Calle 34 # 38-25 Local 1 | 3024820103
**BARRANQUILLA:** Ofero Santo Domingo — Calle 90 | Calle 90 # 2B-40 Local 2 | 3234359174
**BARRANQUILLA:** Ofero Simón Bolívar — Calle 19 | Calle 19 # 6C-16 | 3233314083
**GALAPA:** Ofero Galapa — Calle 10 | Calle 10 # 22-69 Local 2 | 3008314317
**LURUACO:** Ofero Luruaco — Calle 17 | Calle 17 # 21-14 - Frente al Parque | 3206338184
**MALAMBO:** Ofero Malambo — Calle 10 | Calle 10 # 17-76 | 3022058229
**PUERTO COLOMBIA:** Ofero Puerto Colombia — Calle 2 | Calle 2 # 7-35 | 3012263986
**SABANALARGA:** Ofero Sabanalarga Cra 16 | Carrera 16 # 30-07 | 3016853426
**SANTO TOMÁS:** Ofero Santo Tomás — Carrera 11 | Carrera 11 # 9-21 Local 2 | 3104774788
**SOLEDAD:** Ofero Los Robles — Calle 77 | Calle 77 # 15A-22 - CC Placita Los Robles | 3122073650
**SOLEDAD:** Ofero Plaza del Sol | Carrera 32 # 30-15 | 3022188175
**SOLEDAD:** Ofero Soledad — Calle 18 | Calle 18 # 28A-29 | 3012870707

### BOLÍVAR
**CARMEN DE BOLÍVAR:** Ofero Carmen de Bolívar — Calle 25 | Calle 25 # 41-77 | 3207400556
**CARTAGENA:** Ofero Basurto — Calle 30 | Calle 30 # 32A-02 | 3019105958
**CARTAGENA:** Ofero Bosque — Avenida El Bosque | Av. El Bosque - Transversal 54, Tacarigua Mz 1 Lote 9 | 3243933390
**CARTAGENA:** Ofero Cartagena Centro — Calle 32 | Calle 32 # 10-85 - Av. Daniel Lemaitre | 3246363487
**CARTAGENA:** Ofero CC La Castellana | Av. Pedro de Heredia Calle 30 # 30-31 - Sector El Rubí | 3233666004
**CARTAGENA:** Ofero CC Los Ejecutivos | Centro Comercial Los Ejecutivos | 3014179306
**CARTAGENA:** Ofero CC Mall Plaza | Av. Pedro de Heredia Carrera 13 # 31-45 | 3243915396
**CARTAGENA:** Ofero El Pozón — Barrio El Pozón | Transversal 74 # 52-111 Local 1 | 3207484379
**CARTAGENA:** Ofero Gran Manzana | Centro Comercial Gran Manzana | 3236405774
**CARTAGENA:** Ofero La Castellana — Calle 31 | Calle 31 # 63C-92 Local 8 - CC Villa Sandra | 3019578060
**CARTAGENA:** Ofero Pie de la Popa — Calle 32 | Calle 32 # 21-131 Lote B - Av. Pedro de Heredia | 3006532525
**MAGANGUÉ:** Ofero Magangué — Calle 16 | Calle 16 # 11-12 Piso 1 | 3019765281
**MOMPOX:** Ofero Santa Cruz de Mompox — Calle 17 | Calle 17 # 3-28 - Callejón El Tejar | 3104777052
**TURBACO:** Ofero Turbaco — Carretera Troncal | Manzana A, Lote 2 - La Granja - Carretera Troncal | 3146309115

### BOYACÁ
**PUERTO BOYACÁ:** Ofero Puerto Boyacá — Carrera 2 | Carrera 2 # 11-44 | 3137023511
**TUNJA:** Ofero Tunja — Carrera 11 | Carrera 11 # 16-102 - Centro | 3227113599

### CALDAS
**LA DORADA:** Ofero La Dorada Cra 2 | Carrera 2 # 14-08 | 3218991857
**MANIZALES:** Ofero Manizales — Carrera 22 | Carrera 22 # 17-58 - Centro | 3148501400

### CAQUETÁ
**FLORENCIA:** Ofero Florencia — Calle 13 | Calle 13 # 10-33 | 3016569381

### CASANARE
**YOPAL:** Ofero Yopal Calle 24 | Calle 24 # 21-11 | 3144519299
**YOPAL:** Ofero Yopal Centro — Carrera 19 | Carrera 19 # 11-86 - Centro | 3222529669

### CESAR
**AGUACHICA:** Ofero Aguachica — Calle 5 | Calle 5 # 18-63 | 3122052518
**BECERRIL:** Ofero Becerril — Carrera 5 | Carrera 5 # 11-14 - Avenida Principal | 3218507126
**BOSCONIA:** Ofero Bosconia — Calle 18 | Calle 18 # 17A-55 | 3226707547
**CODAZZI:** Ofero Codazzi — Calle 19 | Calle 19 # 15-114 Local 2 | 3226605797
**CURUMANÍ:** Ofero Curumaní — Carretera Central | Carretera Central # 17-05 | 3122060167
**LA JAGUA:** Ofero La Jagua — Carretera Central | Carretera Central - Al lado del D1 | 3122067820
**LA LOMA:** Ofero La Loma — Calle 10 | Calle 10 # 12-104 Esquina | 3234791624
**VALLEDUPAR:** Ofero 1 de Mayo — Carrera 18 | Carrera 18D Calle 25 Esquina # 24-50 - Simón Bolívar | 3046520272
**VALLEDUPAR:** Ofero Calle 17 | Calle 17 # 13-68 Local 4 | 3104589426
**VALLEDUPAR:** Ofero El Palacio — Diagonal 16 | Diagonal 16 # 14-25 | 3104585087
**VALLEDUPAR:** Ofero El Tractor — Carrera 7A | Carrera 7A # 20D-36 | 3019105957
**VALLEDUPAR:** Ofero Glorieta de los Músicos — Transversal 18 | Transversal 18B # 20B-73 Local 1 | 3024267813
**VALLEDUPAR:** Ofero La 17 con 12 — Calle 17 | Calle 17 # 12-61 | 3001948686
**VALLEDUPAR:** Ofero Los Manguitos — Diagonal 21 | Diagonal 21 # 19 - Local 10 - Los Manguitos | 3018652306
**VALLEDUPAR:** Ofero Simón Bolívar — Carrera 18 | Carrera 18D Calle 25 Esquina | 3001948686
**VALLEDUPAR:** Ofero Tres Postes — Calle 6C | Calle 6C # 16-105 - Tres Postes | 3019106300
**VALLEDUPAR:** Ofero Villalba — Transversal 19 | Transversal 19 # 2D-218 - Villalba | 3226628767
**VALLEDUPAR:** Ofero Zona Móvil — Carrera 8 | Carrera 8 # 17-17 Local 25 | 3015294017

### CÓRDOBA
**CERETÉ:** Ofero Cereté — Calle 14 | Calle 14 # 15-32 | 3023589181
**CHINÚ:** Ofero Chinú — Carrera 7 | Carrera 7 Calle 19-26 | 3206624281
**CIÉNAGA DE ORO:** Ofero Ciénaga de Oro — Carrera 15 | Carrera 15 # 7-86 - Calle del Comercio | 3001948686
**LORICA:** Ofero Lorica — Calle 4A | Calle 4A # 23A-12 | 3013118311
**MONTELÍBANO:** Ofero Montelíbano | Próximamente | 3001948686
**MONTERÍA:** Ofero Buenavista — Calle 15 | Calle 15 # 7-55 Local 1 - Barrio Buenavista | 3234366340
**MONTERÍA:** Ofero CC Nuestro Montería | Transversal 29 # 29-69 - CC Nuestro Montería | 3122054558
**MONTERÍA:** Ofero Montería Centro — Carrera 4 | Carrera 4 # 30-58 | 3024267768
**MONTERÍA:** Ofero Montería El Dorado — Carrera 9W | Carrera 9W Calle 23-65 - Barrio El Dorado | 3234353977
**MONTERÍA:** Ofero Montería La 41 — Carrera 10A | Carrera 10A # 41-10 | 3114235922
**MONTERÍA:** Ofero Montería La Granja — Transversal 5 | Transversal 5 # 12-06 | 3046676575
**PLANETA RICA:** Ofero Planeta Rica — Carrera 7 | Carrera 7 # 10-64 - CC Planeta Plaza Local 13 | 3001948686
**SAHAGÚN:** Ofero Sahagún — Calle 18 | Calle 18 Carrera 1A - Avenida Hospital | 3159411645

### CUNDINAMARCA
**BOGOTÁ:** Ofero Álamos — Calle 72 | Calle 72 # 103-12 | 3135176995
**BOGOTÁ:** Ofero Avenida Boyacá | Avenida Boyacá # 68B-41 | 3214198411
**BOGOTÁ:** Ofero Avenida Cali Aures | Calle 137B # 104-35 | 3205959536
**BOGOTÁ:** Ofero Avenida Cra 30 | Avenida Carrera 30 # 41-25 - EDS Texaco | 3228844750
**BOGOTÁ:** Ofero Calle 80 | Avenida Calle 80 # 82A-22 | 3209792639
**BOGOTÁ:** Ofero Calle 85 | Carrera 15 # 85-19 Local 1 | 3228888613
**BOGOTÁ:** Ofero Cedritos — Calle 134 | Calle 134 # 19-46 | 3236396681
**BOGOTÁ:** Ofero Centro de Experiencia Kennedy | Calle 78 # 39A Sur-82 | 3046663623
**BOGOTÁ:** Ofero Centro de Experiencia Niza — Avenida Suba | Avenida Suba # 128A-60 | 3146044862
**BOGOTÁ:** Ofero Chapinero — Calle 57 | Calle 57 # 13-42 Local 1 | 3114435753
**BOGOTÁ:** Ofero Escuela Militar — Calle 80 | Calle 80 # 56-39 | 3228095995
**BOGOTÁ:** Ofero Fontibón — Carrera 100 | Carrera 100 # 20C-07 | 3219133147
**BOGOTÁ:** Ofero Galerías — Carrera 24 | Carrera 24 # 51-04 Esquina | 3102412888
**BOGOTÁ:** Ofero La 74 — Calle 74 | Calle 74 # 15-12 | 3146044916
**BOGOTÁ:** Ofero La Alquería — Autopista Sur | Autopista Sur # 52-10 | 3113585986
**BOGOTÁ:** Ofero La Campiña — Carrera 92 | Carrera 92 # 147B-11 - Barrio Suba | 3113585988
**BOGOTÁ:** Ofero La Estrada Av Rojas | Carrera 70 # 64-74 Local 2 | 3113587220
**BOGOTÁ:** Ofero Las Américas — Avenida Las Américas | Avenida Las Américas (Calle 6A) # 71A-60 | 3228836931
**BOGOTÁ:** Ofero Las Ferias — Calle 72 | Calle 72 # 76-84 | 3113585990
**BOGOTÁ:** Ofero Lourdes Chapinero — Calle 13 | Calle 13 # 60 Esquina | 3113587225
**BOGOTÁ:** Ofero Niza — Transversal 60 | Transversal 60 # 127D-06 Local 1 | 3228834722
**BOGOTÁ:** Ofero Prado Veraniego — Calle 130 | Calle 130 # 45-35 | 3146044895
**BOGOTÁ:** Ofero Restrepo — Transversal 18 Sur | Transversal 18 Sur # 14A-53 | 3106642901
**BOGOTÁ:** Ofero Ricaurte — Calle 13 | Calle 13 # 28-25 | 3228836946
**BOGOTÁ:** Ofero Suba — Carrera 50 | Carrera 50 # 91-92 | 3114464212
**BOGOTÁ:** Ofero Venecia — Carrera 53 Sur | Carrera 53 Sur # 49-40 | 3113621424
**CAJICÁ:** Ofero Cajicá — Carrera 5 | Carrera 5 # 3-177 Sur Local 102 | 3001948686
**FUSAGASUGÁ:** Ofero Fusagasugá Multimarca — Calle 8 | Calle 8 Av. Las Palmas # 5-49 | 3138002879

### HUILA
**NEIVA:** Ofero Neiva Centro — Calle 5 | Calle 5 # 7-06 Local 1 | 3172141533
**NEIVA:** Ofero Neiva Cra 6 | Carrera 6 # 8-10 | 3204075736
**PITALITO:** Ofero Pitalito Centro — Carrera 4 | Carrera 4 # 3-79 | 3223668589
**PITALITO:** Ofero Pitalito Red Phone — Carrera 4 | Carrera 4 # 4-03 Esquina | 3126242387

### LA GUAJIRA
**FONSECA:** Ofero Fonseca — Diagonal 12 | Diagonal 12 # 21-64 | 3189422983
**MAICAO:** Ofero Maicao — Calle 12 | Calle 12 # 8-33 | 3126671485
**RIOHACHA:** Ofero Riohacha — Carrera 15 | Carrera 15 # Calle 15-49 Apto 1 | 3235639794
**SAN JUAN DEL CESAR:** Ofero San Juan del Cesar — Carrera 6 | Carrera 6 # 2 Sur-18 Local 2 | 3148589796

### MAGDALENA
**CIÉNAGA:** Ofero Ciénaga — Carrera 13 | Carrera 13 # 18-29 | 3233224643
**EL BANCO:** Ofero El Banco — Calle 8 | Calle 8 Carrera 2-89 Apto 3 | 3219573558
**FUNDACIÓN:** Ofero Fundación — Carrera 8 | Carrera 8 # 9-82 | 3019767616
**PIVIJAY:** Ofero Pivijay — Calle 17 | Calle 17 Carrera 12-02 - Barrio La Bonga | 3004672046
**PLATO:** Ofero Plato — Calle 12 | Calle 12 Carrera 16-4 - Barrio El Carmen | 3107025563
**SALAMINA:** Ofero Salamina — Calle 5 | Calle 5 # 6-52 - Barrio Arriba | 3004672046
**SANTA MARTA:** Ofero 11 de Noviembre — Calle 30 | Calle 30 # 74-41 | 3013673299
**SANTA MARTA:** Ofero Éxito Buenavista | Calle 32 # 29A-500 - Éxito Buenavista | 3113487505
**SANTA MARTA:** Ofero Éxito Centro | Éxito Centro Santa Marta | 3002749339
**SANTA MARTA:** Ofero Ferrocarril — Carrera 8C | Carrera 8C # 15-03 - Barrio El Pradito | 3234361281
**SANTA MARTA:** Ofero La Bomba / Las Palmitas — Calle 24 | Calle 24 # 11-44 - Barrio Bolívar | 3117010345
**SANTA MARTA:** Ofero Rodadero — Calle 12A | Calle 12A # 17A-7 | 3012262625

### META
**VILLAVICENCIO:** Ofero Villavicencio Catama — Calle 35 | Calle 35 # 20D-06 - Avenida Catama | 3103368966
**VILLAVICENCIO:** Ofero Villavicencio Centro — Calle 53 | Calle 53 # 20D-07 | 3103368966
**VILLAVICENCIO:** Ofero Villavicencio La 40 — Avenida 40 | Avenida 40 # 26C-37 | 3046810874

### NORTE DE SANTANDER
**CÚCUTA:** Ofero Cúcuta Diagonal | Diagonal Santander # 8-16 | 3001948686
**CÚCUTA:** Ofero Cúcuta Principal — Diagonal Santander | Diagonal Santander # 8-28 | 3132715503
**CÚCUTA:** Ofero Gran Colombia — Avenida Gran Colombia | Av. Gran Colombia 5E | 3134352889
**CÚCUTA:** Ofero Kesla Cúcuta Diagonal | Diagonal Santander # 8-16 - Fuente Luminosa | 3132715503
**CÚCUTA:** Ofero Kesla Malecón — Avenida 9E | Avenida 9E # 11-131 - Malecón | 3118269681
**OCAÑA:** Ofero Ocaña — Calle 7 | Calle 7 # 29-74 - Av. Francisco Fernández de Contreras | 3170254890
**PAMPLONA:** Ofero Pamplona — Carrera 5 | Carrera 5 # 8B-24 Local A - Edificio García Álvarez | 3125310926

### QUINDÍO
**ARMENIA:** Ofero Armenia — Carrera 19 | Carrera 19 # 12-26 | 3019721050
**ARMENIA:** Ofero Electrimotors Armenia — Carrera 18 | Carrera 18 # 21-10 Local 2 | 3116515100

### RISARALDA
**PEREIRA:** Ofero Dosquebradas — Carrera 16 | Dosquebradas Carrera 16 # 37-28 | 3128700256
**PEREIRA:** Ofero Pereira — Avenida 30 de Agosto | Av. 30 de Agosto # 36-47 | 3103559985

### SAN ANDRÉS
**SAN ANDRÉS:** Ofero San Andrés — Avenida Las Américas | Av. Las Américas # 3-165 - San Andrés Isla | 3003412506

### SANTANDER
**BARRANCABERMEJA:** Ofero Barrancabermeja — Calle 50 | Calle 50 # 13-02 | 3122355687
**BUCARAMANGA:** Ofero Cabecera — Calle 51 | Calle 51 # 33-24 | 3159607627
**BUCARAMANGA:** Ofero Centro — Carrera 15 | Carrera 15 # 37-27 - Centro | 3181227935
**BUCARAMANGA:** Ofero Floridablanca — Carrera 8 | Carrera 8 # 5-60 - Parque Principal | 3002736849
**BUCARAMANGA:** Ofero Girón — Avenida Cañayes | Av. Cañayes Calle 25 # 21B-114 | 3209272641
**BUCARAMANGA:** Ofero La 21 — Carrera 21 | Carrera 21 # 37-16 | 3219409049
**BUCARAMANGA:** Ofero La 27 — Calle 55A | Calle 55A # 27-04 | 3209272626
**BUCARAMANGA:** Ofero La Isla — Carrera 18 | Carrera 18 # 54-60 | 3209267267
**BUCARAMANGA:** Ofero Parque de los Niños — Carrera 27 | Carrera 27 # 34-66 | 3014377928
**BUCARAMANGA:** Ofero Pedregosa — Carrera 33 | Carrera 33 # 94-23 | 3045809629
**BUCARAMANGA:** Ofero Provenza — Carrera 27 | Carrera 27 # 104-11 Local 2 y 3 | 3184849993
**BUCARAMANGA:** Ofero Sotomayor — Carrera 33 | Carrera 33 # 58-16 | 3202465871
**SAN GIL:** Ofero San Gil — Carrera 10 | Carrera 10 # 9-67 - Centro | 3507853621

### SUCRE
**COROZAL:** Ofero Corozal — Carrera 26 | Carrera 26 # 32-15 | 3242670796
**COVEÑAS:** Ofero Coveñas — Calle 9C | Calle 9C # 24-22 | 3246803632
**MAJAGUAL:** Ofero Majagual — Calle 5 | Calle 5 # 19-21 - Centro | 3104788770
**SINCELEJO:** Ofero Alfonso López — Carrera 19 | Carrera 19 # 28A-32 | 3005007262
**SINCELEJO:** Ofero Av. Luis Carlos Galán | Calle 28 # 22B-90 | 3188205626
**SINCELEJO:** Ofero Sincelejo Las Peñitas — Carrera 25 | Carrera 25 # 21-60 - Av. Las Peñitas | 3004361782

### TOLIMA
**IBAGUÉ:** Ofero Ibagué — Carrera 5 | Carrera 5 # 19-141 - Local Esquina | 3228940555

### VALLE DEL CAUCA
**BUENAVENTURA:** Ofero Buenaventura — Carrera 6 | Carrera 6 # 2-36 Local 102 | 3107078548
**BUGA:** Ofero Buga — Carrera 9 | Carrera 9 # 14-01 Esquina | 3024296633
**CALI:** Ofero Cali Carrera 23 | Calle 15 # 23-07 - Aranjuez | 3145811079
**CALI:** Ofero Cali Centro — Carrera 5 | Carrera 5 # 15-49 | 3151812511
**CALI:** Ofero Cali Cra 15 | Carrera 15 # 10-49 | 3169380086
**CALI:** Ofero Cali Norte — Avenida 3 Norte | Avenida 3 Norte # 47N-48 Local 27 | 3126809691
**CALI:** Ofero Cali Roosevelt — Avenida Roosevelt | Av. Roosevelt # 25-70 | 3216433681
**CALI:** Ofero Calima — Carrera 5N | Carrera 5N # 68N-36 - Calima | 3126809692
**CALI:** Ofero Cañaveralejo — Carrera 57 | Carrera 57 # 40-49 - Edificio Atalanta | 3128812938
**CALI:** Ofero Centro Cra 8 — Carrera 8 | Carrera 8 # 22A Local 16 - Barrio Obrero | 3108657160
**CALI:** Ofero La 14 Cali — Calle 14 | Calle 14 # 4-19 | 3046063509
**CALI:** Ofero La 66 Cali — Calle 13 | Calle 13 # 65C-42 Local 2 | 3043958526
**CALI:** Ofero Marroquín — Carrera 26 | Carrera 26 M1 # 83-10 - Marroquín 2 | 3505344053
**CALI:** Ofero Valle Grande — Carrera 23 | Carrera 23 # 89-19 - Valle Grande Local 8 | 3244472336
**CARTAGO:** Ofero Cartago — Calle 10 | Calle 10 # 9-83 | 3116805612
**JAMUNDÍ:** Ofero Jamundí — Calle 10 | Calle 10 # 10-63 Local 5 - Edificio Ligia | 3043958549
**PALMIRA:** Ofero Palmira — Carrera 33A | Carrera 33A # 30-61 | 3207716424
**TULUÁ:** Ofero Tuluá — Calle 27 | Calle 27 # 20-29 - Barrio Centro | 3128120244

---

## LINEAMIENTOS DE CONSTRUCCIÓN

### Layout de la página
```
┌─────────────────────────────────┐
│  HEADER: Logo OFERO + Tagline   │
├─────────────────────────────────┤
│  HERO: Título + descripción     │
├─────────────────────────────────┤
│  SECCIÓN DE FILTROS:            │
│  [ Select Departamento ]        │
│  [ Select Ciudad       ]        │
│  [ Select Tienda       ]        │
├─────────────────────────────────┤
│  CARD DE RESULTADO              │
│  (visible solo al seleccionar)  │
├─────────────────────────────────┤
│  FOOTER: Línea nacional OFERO   │
└─────────────────────────────────┘
```

### Textos sugeridos
- **Título hero:** `"Encuentra tu tienda OFERO más cercana"`
- **Subtítulo:** `"Selecciona tu departamento, ciudad y sede para ver la información de contacto."`
- **Footer:** `"¿Necesitas ayuda? Llama a nuestra línea nacional: 300 1948686"`

### Card de resultado — campos y formato
```
┌──────────────────────────────────┐
│  ▌ NOMBRE DE LA TIENDA           │  ← Verde, ExtraBold, prominente
│    Ciudad · Departamento         │  ← Gris claro, SemiBold
├──────────────────────────────────┤
│  📍  Dirección completa          │  ← Blanco / Gris claro
│  📞  321 5261638                 │  ← Verde, enlace tel:
├──────────────────────────────────┤
│  [ 🗺 ¿Cómo llegar? ]           │  ← Botón secundario Google Maps
└──────────────────────────────────┘
```

### Google Maps link
```javascript
const mapsUrl = `https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(tienda.direccion + ', ' + ciudad + ', Colombia')}`;
```

### Teléfono clickeable
```html
<a href="tel:+57${tienda.telefono}">📞 ${tienda.telefonoDisplay}</a>
```

---

## REQUISITOS TÉCNICOS

- **Entregable:** Un único archivo `index.html` autocontenido.
- **Sin frameworks:** Vanilla HTML, CSS y JS. Sin React, Vue, Bootstrap ni jQuery.
- **Responsive:** Funcional en móvil (mínimo 320px) y escritorio.
- **Accesibilidad básica:** Labels en selects, roles ARIA en card de resultado, contraste suficiente.
- **Sin backend:** Todos los datos embebidos en el JS del mismo archivo.
- **Google Fonts:** Única dependencia externa permitida.

---

## RESUMEN RÁPIDO

```
App:        Localizador de tiendas OFERO Colombia
Tipo:       Single HTML file, sin dependencias
UX:         Filtros en cascada → Departamento → Ciudad → Tienda → Card
Colores:    #1D1E21 fondo | #70D84A verde | #E8EAEA texto
Fuente:     Manrope 400/600/800
Tema:       Oscuro con acentos verdes
Datos:      199 tiendas embebidas en JS
Línea nac:  300 1948686
```
