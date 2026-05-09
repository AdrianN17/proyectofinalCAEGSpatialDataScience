# Proyecto B02 — Humedales Cercanos a Zonas Urbanas en el Perú

**Pregunta:** ¿Cuántos humedales del Perú se encuentran a menos de 5 km de un casco urbano y qué nivel de exposición presentan?

---

## Origen de datos

| Capa | Fuente | Descripción | URL |
|---|---|---|---|
| Cascos urbanos | INEI / IGN — Perú (2024) | Polígonos de zonas urbanizadas a nivel distrital | https://www.geogpsperu.com/2018/09/casco-urbano-100k-poblacion-urbana-ign.html |
| Humedales | Ministerio del Ambiente — MINAM (2024) | Polígonos de ecosistemas de humedales del Perú | https://www.geogpsperu.com/2018/02/humedales-ramsar-shapefile-minam.html |
| Departamentos | IGN — Perú | Límites político-administrativos departamentales | https://www.geogpsperu.com/2018/02/limite-departamental-politico-shapefile.html |

Los archivos se distribuyen como shapefiles comprimidos en ZIP y se descargan automáticamente desde Google Drive al ejecutar el script.

---

## Licencias

| Recurso | Licencia |
|---|---|
| Datos geoespaciales INEI / IGN / MINAM | Uso público — datos abiertos del Estado peruano |
| Librerías Python (GeoPandas, Folium, Matplotlib, etc.) | BSD / MIT — código abierto |
| Código del proyecto | Libre para uso académico |

---

## Pasos para reproducir

**Requisitos:** Python 3.8+, conexión a internet.

**1. Instalar dependencias**
```bash
pip install geopandas folium matplotlib seaborn shapely contextily adjustText plotly requests branca
```

**2. Ejecutar el script**
```bash
python proyecto_b02_diplomado.py
```
> También puede abrirse directamente en Google Colab desde el enlace:  
> https://colab.research.google.com/drive/1IH7JlMiyP9JXVrPi6DjtZxbdXi2rQFTd

**3. El script realiza automáticamente:**
- Descarga y descompresión de los 3 shapefiles desde Google Drive
- Limpieza y selección de columnas relevantes
- Reporte de calidad de datos (nulos, vacíos, geometrías inválidas)
- Cálculo de buffer de **5 km** alrededor de cada casco urbano (EPSG:32718)
- Identificación de humedales dentro del buffer mediante spatial join
- Generación de estadísticas y gráficos (barras, torta, mapa interactivo)

**4. Salida generada**

| Archivo | Descripción |
|---|---|
| `mapa_humedales.html` | Mapa interactivo con todas las capas del análisis |

---

> **Resultado principal:** El **73.4 %** de los humedales evaluados se encuentran a menos de 5 km de una zona urbana. Los departamentos con mayor exposición son **Ica, La Libertad y Piura**.
