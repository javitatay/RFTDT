# RF · TDT España — Frecuencias UHF

Herramienta de consulta de frecuencias TDT para técnicos de microfonía inalámbrica y sistemas RF en producciones en directo.

## Contenido del repositorio

```
rf-tdt-espana/
├── index.html   → interfaz web completa
├── tdt.csv      → base de datos de frecuencias (CNAF / MINETUR)
└── README.md
```

## Uso

### GitHub Pages (recomendado)

1. Sube los dos archivos (`index.html` y `tdt.csv`) al repositorio
2. Activa GitHub Pages en **Settings → Pages → Branch: main → / (root)**
3. La web estará disponible en `https://tu-usuario.github.io/nombre-repo/`

El HTML carga `tdt.csv` automáticamente al abrirse. No requiere servidor ni dependencias externas.

### En local

Abre `index.html` directamente en Chrome o Firefox. Si el navegador bloquea el `fetch` local por CORS, arrastra el archivo `tdt.csv` al área que aparece en pantalla.

## Actualizar la base de datos

Solo tienes que sustituir `tdt.csv` por una versión actualizada manteniendo el mismo formato de columnas:

```
Comunidad Autónoma, Provincia, Demarcación, Ámbito de Cobertura, Canal, Frecuencia (MHz)
```

Los campos Canal y Frecuencia admiten múltiples valores separados por comas dentro de la misma celda (entre comillas si el campo contiene comas).

## Funcionalidades

- **Verificador de frecuencia** — introduce la frecuencia central de tu micrófono y comprueba si hay conflicto con algún canal TDT activo en la selección actual
- **Visualizador de espectro** — representación gráfica de los canales UHF entre 470 y 694 MHz
- **Filtros en cascada** — CC.AA. → Provincia → Demarcación → Ámbito de cobertura
- **Tabla ordenable** — clic en cualquier cabecera para ordenar
- **Exportar CSV** — descarga la selección filtrada como archivo CSV

## Datos

Fuente: Plan Nacional de Atribución de Frecuencias (CNAF) / Ministerio para la Transformación Digital y de la Función Pública.

Banda UHF IV/V · DVB-T · 470–694 MHz · 8 MHz por canal · Frecuencia central ± 4 MHz
