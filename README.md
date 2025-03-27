## Prueba técnica

### Resumen

Se ha procedido a la confección de un modelo geográfico que permite cuantificar el grado de accesibilidad cultural de hasta 3 municipios ubicados en la provincia de Sevilla: Camas, Valencina de la Concepción y el propio municipio de Sevilla. Para ello nos basamos en la población y el tipo de servicio/equipamiento cultural en cada una de estas entidades poblacionales.

No menos relevante ha sido la generación de isócronas en función del tiempo de viaje a pie establecido para cada servicio: museos, bibliotecas y centros culturales (puesto que la búsqueda de información espacial vinculada con teatros y/o auditorios no ha resultado satisfactoria), considerando el tramo de población de cada municipio.

El resultado final no ha sido otro que la generación de un índice estandarizado que considera el área de las isócronas generadas junto con el área del núcleo de población, siendo ajustado por el tamaño poblacional de cada uno de los municipios.

### Municipio y Población

| Municipio | Población |
|-----------|------------|
| Valencina de la Concepción | 7,920 |
| Camas | 27,645 |
| Sevilla | 684,342 |

### Fuentes de información

Se ha procedido a descargar información geográfica procedente del Instituto de Estadística y Cartografía de Andalucía:
[Datos espaciales de referencia de Andalucía](https://www.juntadeandalucia.es/institutodeestadisticaycartografia/dega/datos-espaciales-de-referencia-de-andalucia-dera)

- **Término municipal:** tipo poligonal en formato shapefile
- **Núcleos de población:** tipo poligonal en formato shapefile
- **Museos:** tipo puntual en formato shapefile
- **Bibliotecas y centros culturales:** tipo puntual en formato shapefile

Todos ellos poseen el sistema de referencia de coordenadas EPSG: 25830.

En última instancia, se consultaron en el [Instituto Nacional de Estadística](https://www.ine.es/) los datos de población de los 3 municipios implicados en el presente análisis.

### Lenguaje de programación, software y API

Para la elaboración de este estudio hemos empleado el lenguaje de programación **Python (v3.12)** a través del software de código abierto **Jupyter Notebook**. Para la generación de isócronas ha sido fundamental el uso de la API **[OpenRouteService](https://openrouteservice.org/)**.

También se ha empleado **QGIS (v3.34)** para la visualización de capas espaciales y detección de anomalías en geometría y sistemas geodésicos.

### Librerías utilizadas

- `geopandas` → Para trabajar con datos geoespaciales.
- `matplotlib` → Para visualización de datos.
- `pandas` → Para manipulación de datos en tablas.
- `requests` → Para hacer solicitudes a la API de OpenRouteService.
- `shapely` → Para manejar geometrías (puntos, polígonos, etc.).
- `tabulate` → Para mostrar tablas de datos de forma más legible.

### Metodología

#### 1. Clasificación de municipios por tamaño poblacional

Se han clasificado los municipios en tres categorías:

- **Pequeño** (<10,000 habitantes)
- **Mediano** (10,000 - 49,999 habitantes)
- **Grande** (≥50,000 habitantes)

Esta clasificación permite ajustar los umbrales de viaje y facilitar el análisis comparativo entre municipios de distintos tamaños.

#### 2. Asignación de tiempos de viaje según tamaño del municipio y tipo de equipamiento cultural

| Categoría de municipio | Bibliotecas | Museos |
|-----------------------|------------|--------|
| Pequeño (<10,000 hab.) | 10 min | 15 min |
| Mediano (10,000 - 49,999 hab.) | 15 min | 20 min |
| Grande (≥50,000 hab.) | 20 min | 25 min |

Los tiempos de viaje se han definido en función de:

- **Tamaño del municipio:** Municipios más grandes tienden a tener población más dispersa.
- **Tipo de servicio cultural:** Los museos son menos frecuentes y requieren más tiempo de acceso.

### Conclusión

El análisis realizado ha permitido evaluar la accesibilidad cultural en los municipios seleccionados, estableciendo un índice basado en la relación entre isócronas de viaje y población. Esto puede ser utilizado para futuras estrategias de mejora en la distribución de equipamientos culturales.
