# RF · TDT España — Frecuencias UHF

**Herramienta de consulta de frecuencias** para técnicos de microfonía inalámbrica y sistemas RF en producciones en directo. Muestra qué canales UHF ocupa la TDT en cada demarcación de España, con mapa interactivo de selección gradual, visualización del espectro libre y ocupado, verificador de conflictos y calculadora de intermodulación con diagrama explicativo interactivo.

🌐 **[javitatay.github.io/RFTDT](https://javitatay.github.io/RFTDT/)**

---

### Badges

![version](https://img.shields.io/badge/version-3.5.0-blue) ![standard](https://img.shields.io/badge/estándar-DVB--T-green) ![banda](https://img.shields.io/badge/banda-UHF%20470–694%20MHz-orange) ![license](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey) ![datos](https://img.shields.io/badge/datos-abril%202026-red)

---

## Descripción

Cuando se trabaja con microfonía inalámbrica en un evento o producción en directo, es imprescindible conocer qué frecuencias UHF están ocupadas por la TDT en la zona de trabajo para evitar interferencias. Esta herramienta centraliza esa información y permite consultarla de forma visual e intuitiva, con selección por mapa, filtros en cascada y verificación de conflictos en tiempo real.

El proyecto no requiere servidor, instalación ni cuenta. Funciona directamente en el navegador cuando se sirve desde un servidor HTTP (GitHub Pages o servidor local).

---

## Funcionalidades

- **Geolocalización automática** — detecta la ubicación del dispositivo y preselecciona automáticamente la Comunidad Autónoma y provincia
- **Vista de canales activos** — grid visual con número de canal, frecuencia central y rango ocupado para la demarcación seleccionada; los conflictos con el micrófono se marcan en rojo al instante
- **Mapa de espectro** — representación gráfica del espectro UHF 470–694 MHz que muestra en **rojo** los canales TDT ocupados y en **verde** los canales libres disponibles, con tooltip de detalle al pasar el cursor
- **Mapa interactivo con zoom gradual** — selección en 4 pasos: Comunidad Autónoma → Provincia → Demarcación → Ámbito; al seleccionar cada nivel el mapa hace zoom automático (`flyToBounds`) a la zona correspondiente; al limpiar la selección vuelve a la vista general de España
- **Markers de demarcación** — al seleccionar una provincia aparecen en el mapa marcadores circulares orientativos para cada demarcación; el marcador seleccionado se rellena en verde; un clic sobre él selecciona la demarcación directamente sin usar el panel lateral. Las coordenadas son aproximadas (extraídas de Google Maps por nombre de municipio) y se irán refinando con datos reales de repetidores
- **Panel lateral contextual** — muestra las provincias disponibles como chips al seleccionar una CA, el número de ámbitos por demarcación al seleccionar provincia, y el número de canales ocupados al completar la selección
- **Filtros en cascada** — filtra por Comunidad Autónoma → Provincia → Demarcación → Ámbito de cobertura, sincronizados con el mapa
- **Verificador de frecuencia** — introduce la frecuencia central de tu micrófono y comprueba si entra en conflicto con algún canal TDT activo en la demarcación seleccionada
- **Exportar CSV** — exporta los canales UHF (ocupados y libres) de la selección actual en formato compatible con Shure Wireless Workbench y Sennheiser WSM/Sundbase
- **Tabla ordenable** — ordena los resultados por cualquier columna (canal, frecuencia, rango, demarcación...)
- **Calculadora de intermodulación IM3** — herramienta independiente para comprobar si las frecuencias de un sistema de micrófonos generan productos de intermodulación de tercer orden entre sí, con diagrama explicativo interactivo integrado

---

## Calculadora de intermodulación IM3

La página `intermodulacion.html` combina la calculadora con un **diagrama explicativo interactivo** pensado para técnicos que necesitan entender o enseñar el fenómeno en campo:

### Diagrama explicativo

- **3 pasos conceptuales** — explica de forma progresiva qué ocurre: dos transmisores activos generan señales fantasma (productos IM3) que pueden coincidir con otras frecuencias del sistema
- **Simulador interactivo** — dos sliders permiten mover Fa y Fb libremente por la banda UHF (470–690 MHz) en pasos de **25 kHz**, observando en tiempo real los productos IM₁/IM₂, la separación Δ, la visualización en canvas y la alerta de conflicto

### Calculadora

Introduciendo las frecuencias reales del sistema (hasta 30 dispositivos), calcula todos los productos IM3 por par y muestra resumen de conflictos con fórmula exacta, visualización de espectro y tabla cruzada completa.

---

## Datos técnicos

| Campo | Valor |
|---|---|
| **Estándar** | DVB-T (TDT) |
| **Banda** | UHF Banda IV / V |
| **Rango** | 470 – 694 MHz |
| **Canales** | CH21 – CH48 (28 canales de 8 MHz) |
| **Rango ocupado por canal** | Frecuencia central ± 4 MHz |
| **Paso de frecuencia (microfonía)** | 25 kHz (0.025 MHz) |
| **Tolerancia detección conflicto IM** | ± 25 kHz |
| **Cobertura geográfica** | España peninsular, Baleares, Canarias, Ceuta y Melilla |
| **Fuente de datos** | CNAF / Ministerio para la Transformación Digital y de la Función Pública |
| **Actualización de datos** | Abril 2026 |
| **Demarcaciones con marker en mapa** | 274 (coordenadas orientativas, pendiente refinamiento) |

---

## Estructura del repositorio

```
RFTDT/
├── index.html            → interfaz principal (diseño + lógica)
├── intermodulacion.html  → calculadora de intermodulación IM3 + diagrama explicativo
├── tdt.csv               → base de datos de frecuencias por demarcación
├── .nojekyll             → desactiva Jekyll en GitHub Pages
└── README.md
```

---

## Uso

La herramienta está disponible en línea y no requiere instalación:

**[javitatay.github.io/RFTDT](https://javitatay.github.io/RFTDT/)**

Para uso local, clona el repositorio y sirve los archivos con cualquier servidor estático:

```bash
git clone https://github.com/javitatay/RFTDT.git
cd RFTDT
npx serve .
# o alternativamente:
python3 -m http.server 8000
```

> **Nota:** abrir `index.html` directamente con doble clic bloquea la carga del CSV por restricciones CORS del navegador. Es necesario usar un servidor local o GitHub Pages.

---

## Actualizar la base de datos

Sustituye `tdt.csv` por una versión actualizada manteniendo el mismo formato de columnas:

```
Comunidad Autónoma, Provincia, Demarcación, Ámbito de Cobertura, Canal, Frecuencia (MHz)
```

Los campos Canal y Frecuencia admiten múltiples valores separados por comas (entre comillas si el campo contiene comas). El HTML parsea y expande automáticamente cada fila en entradas individuales por canal.

---

## Aviso

> **Base de datos actualizada a abril de 2026.** Los datos de canales TDT proceden del CNAF / Ministerio para la Transformación Digital y de la Función Pública. La asignación de frecuencias puede variar: se recomienda verificar con la fuente oficial antes de cada producción y realizar siempre un escaneo RF del espacio de trabajo.

---

## Contacto

**Javier Tatay Rubio**  
📧 j.tatayrubio@edu.gva.es

---

*Herramienta de uso libre para técnicos audiovisuales · 2026*

**Version:** 3.5.0 | **Built with:** Claude AI
