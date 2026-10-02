# Análisis de popularidad musical en Spotify (2020-2025)

Proyecto de análisis de datos con Python y pandas, enfocado en explorar qué variables se relacionan con la popularidad de una canción.

## ¿Qué es este proyecto?

Proyecto creado para practicar la librería pandas aplicándola a un caso de análisis completo: desde la formulación de una pregunta de investigación hasta la limpieza de datos, el cálculo de estadísticas y la comunicación de resultados.

## Pregunta central

¿Cómo el género, la bailabilidad, el día de lanzamiento y la duración se relacionan con la popularidad de una canción a través del tiempo (2020-2025)?

## Sobre el dataset

Este proyecto utiliza un [dataset sintético de streaming de Spotify](https://www.kaggle.com/datasets/beamhonor0911/spotify-artist-streaming-analytics-20202025) descargado desde Kaggle (50,000 filas, 33 columnas).

**Limitación importante**: al ser un dataset sintético (generado artificialmente, no extraído en vivo de la plataforma real), los resultados de este análisis no deben interpretarse como reflejo fiel del comportamiento real de los oyentes de Spotify. El valor de este proyecto está en practicar el *proceso* de análisis de datos, no en producir conclusiones aplicables a la industria musical real.

## Metodología

1. **Validación de datos**: se verificaron nulos, duplicados y valores fuera de rango. El dataset no presentó nulos ni duplicados; el rango de años (2020-2025) fue consistente.
2. **Elección de variable objetivo**: se usó `popularity` en lugar de `stream_count`, ya que esta última está sesgada por el tiempo que una canción lleva disponible en la plataforma.
3. **Género**: se agruparon los géneros con menos de 2,000 canciones en la categoría "Otros" (para evitar promedios poco confiables por tamaño de muestra pequeño), y se calculó promedio, desviación estándar y conteo de `popularity` por grupo, además de su evolución año a año.
4. **Bailabilidad y duración**: al ser variables numéricas continuas, se calculó su correlación de Pearson con `popularity` en lugar de agruparlas en categorías.
5. **Día de lanzamiento**: se comparó el promedio y desviación estándar de `popularity` entre canciones lanzadas en fin de semana vs. entre semana.

A lo largo del análisis se usó deliberadamente el lenguaje de "relación" y "correlación", no de "causa", ya que el método empleado no permite establecer causalidad.

## Hallazgos

 Variable 
 Género : Diferencias de promedio de popularidad menores a 1 punto entre géneros (sobre una desviación estándar de ~16) |
 Bailabilidad (danceability) : Correlación de 0.001 con popularidad 
 Día de lanzamiento (weekend) : Diferencia de promedio de apenas 0.02 puntos entre weekend y entre semana |
 Duración : Correlación de 0.0017 con popularidad 

## Conclusión

Con la información reunida, podemos decir que, a través de los años, la bailabilidad, el género, el día de lanzamiento y la duración no se relacionan de la manera que se pensaría a primera vista (al menos para este dataset sintético). Las diferencias encontradas en todos los casos son demasiado pequeñas frente a la variabilidad interna de cada grupo, lo cual es consistente con la posibilidad de que la columna `popularity` haya sido generada de forma independiente a las demás variables en este dataset específico.

## Herramientas utilizadas

- Python
- pandas
- matplotlib / seaborn
