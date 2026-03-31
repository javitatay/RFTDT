# RF · TDT España — Frecuencias UHF

**Herramienta de consulta de frecuencias** para técnicos de microfonía inalámbrica y sistemas RF en producciones en directo. Muestra qué canales UHF ocupa la TDT en cada demarcación de España, con mapa interactivo de selección gradual, visualización del espectro libre y ocupado, verificador de conflictos y calculadora de intermodulación.

🌐 **[javitatay.github.io/RFTDT](https://javitatay.github.io/RFTDT/)**

---

### Badges

![version](https://img.shields.io/badge/version-3.2.0-blue) ![standard](https://img.shields.io/badge/estándar-DVB--T-green) ![banda](https://img.shields.io/badge/banda-UHF%20470–694%20MHz-orange) ![license](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey)

---

## Descripción

Cuando se trabaja con microfonía inalámbrica en un evento o producción en directo, es imprescindible conocer qué frecuencias UHF están ocupadas por la TDT en la zona de trabajo para evitar interferencias. Esta herramienta centraliza esa información y permite consultarla de forma visual e intuitiva, con selección por mapa, filtros en cascada y verificación de conflictos en tiempo real.

El proyecto no requiere servidor, instalación ni cuenta. Funciona directamente en el navegador cuando se sirve desde un servidor HTTP (GitHub Pages o servidor local).

---

## Funcionalidades

- **Geolocalización automática** — detecta la ubicación del dispositivo y preselecciona automáticamente la Comunidad Autónoma y provincia
- **Vista de canales activos** — grid visual con número de canal, frecuencia central y rango ocupado para la demarcación seleccionada; los conflictos con el micrófono se marcan en rojo al instante
- **Mapa de espectro** — representación gráfica del espectro UHF 470–694 MHz que muestra en **rojo** los canales TDT ocupados y en **verde** los canales libres disponibles, con tooltip de detalle al pasar el cursor
- **Mapa interactivo** — selección gradual por mapa en 4 pasos: Comunidad Autónoma → Provincia → Demarcación → Ámbito; sincronizado con los desplegables
- **Filtros en cascada** — filtra por Comunidad Autónoma → Provincia → Demarcación → Ámbito de cobertura
- **Verificador de frecuencia** — introduce la frecuencia central de tu micrófono y comprueba si entra en conflicto con algún canal TDT activo en la demarcación seleccionada
- **Tabla ordenable** — ordena los resultados por cualquier columna (canal, frecuencia, rango, demarcación...)
- **Calculadora de intermodulación IM3** — herramienta independiente para comprobar si las frecuencias de un sistema de micrófonos generan productos de intermodulación de tercer orden entre sí

---

## Datos técnicos

| Campo | Valor |
|---|---|
| **Estándar** | DVB-T (TDT) |
| **Banda** | UHF Banda IV / V |
| **Rango** | 470 – 694 MHz |
| **Canales** | CH21 – CH48 (28 canales de 8 MHz) |
| **Rango ocupado por canal** | Frecuencia central ± 4 MHz |
| **Cobertura geográfica** | España peninsular, Baleares, Canarias, Ceuta y Melilla |
| **Fuente de datos** | CNAF / Ministerio para la Transformación Digital y de la Función Pública |

---

## Estructura del repositorio

```
RFTDT/
├── index.html            → interfaz principal (diseño + lógica)
├── intermodulacion.html  → calculadora de intermodulación IM3
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

> Esta información puede no estar actualizada en el momento de su uso. Se recomienda realizar un escaneo completo de frecuencias del espacio en el que se desarrollará el show para el conocimiento exacto de las interferencias presentes.

---

## Contacto

**Javier Tatay Rubio**  
📧 j.tatayrubio@edu.gva.es

---

*Herramienta de uso libre para técnicos audiovisuales · 2026*

**Version:** 3.2.0 | **Built with:** Claude AI
