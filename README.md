# RF · TDT España — Frecuencias UHF

**Herramienta de consulta de frecuencias** para técnicos de microfonía inalámbrica y sistemas RF en producciones en directo. Muestra qué canales UHF ocupa la TDT en cada demarcación de España, con verificador de conflictos y visualizador de espectro interactivo.

🌐 **[javitatay.github.io/RFTDT](https://javitatay.github.io/RFTDT/)**

---

### Badges

![version](https://img.shields.io/badge/version-3.0.0-blue) ![standard](https://img.shields.io/badge/estándar-DVB--T-green) ![banda](https://img.shields.io/badge/banda-UHF%20470–694%20MHz-orange) ![license](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey)

---

## Descripción

Cuando se trabaja con microfonía inalámbrica en un evento o producción en directo, es imprescindible conocer qué frecuencias UHF están ocupadas por la TDT en la zona de trabajo para evitar interferencias. Esta herramienta centraliza esa información y permite consultarla, filtrarla y verificar frecuencias en tiempo real.

El proyecto no requiere servidor, instalación ni cuenta. Funciona directamente en el navegador.

---

## Funcionalidades

- **Verificador de frecuencia** — introduce la frecuencia central de tu micrófono y comprueba al instante si entra en conflicto con algún canal TDT activo en la demarcación seleccionada
- **Visualizador de espectro** — representación gráfica del espectro UHF 470–694 MHz con los canales TDT activos y la frecuencia del micrófono superpuesta
- **Filtros en cascada** — filtra por Comunidad Autónoma → Provincia → Demarcación → Ámbito de cobertura
- **Tabla ordenable** — ordena los resultados por cualquier columna (canal, frecuencia, rango, demarcación...)
- **Exportar CSV** — descarga la selección filtrada como archivo CSV para usar en coordinadores RF externos

---

## Datos técnicos

| Campo | Valor |
|---|---|
| **Estándar** | DVB-T (TDT) |
| **Banda** | UHF Banda IV / V |
| **Rango** | 470 – 694 MHz |
| **Anchura de canal** | 8 MHz |
| **Rango ocupado por canal** | Frecuencia central ± 4 MHz |
| **Cobertura geográfica** | España peninsular, Baleares, Canarias, Ceuta y Melilla |
| **Fuente de datos** | CNAF / Ministerio para la Transformación Digital y de la Función Pública |

---

## Estructura del repositorio

```
RFTDT/
├── index.html    → interfaz web completa (diseño + lógica)
├── tdt.csv       → base de datos de frecuencias por demarcación
├── .nojekyll     → desactiva Jekyll en GitHub Pages
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
npx serve .   # o cualquier servidor local
```

> **Nota:** abrir `index.html` directamente con doble clic puede bloquear la carga del CSV por restricciones CORS del navegador. En ese caso, usa un servidor local o arrastra el archivo `tdt.csv` al área que aparece en pantalla.

---

## Actualizar la base de datos

Sustituye `tdt.csv` por una versión actualizada manteniendo el mismo formato de columnas:

```
Comunidad Autónoma, Provincia, Demarcación, Ámbito de Cobertura, Canal, Frecuencia (MHz)
```

Los campos Canal y Frecuencia admiten múltiples valores separados por comas (entre comillas si el campo contiene comas). El HTML parsea y expande automáticamente cada fila en entradas individuales por canal.

---

## Contacto

**Javier Tatay Rubio**  
📧 j.tatayrubio@edu.gva.es

---

*Herramienta de uso libre para técnicos audiovisuales · 2026*

**Version:** 3.0.0 | **Built with:** Claude AI
