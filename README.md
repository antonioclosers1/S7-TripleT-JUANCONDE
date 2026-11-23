# Análisis de clientes ConnectaTel

## Objetivo del proyecto

ConnectaTel es una empresa de telecomunicaciones en Latinoamérica. Este proyecto analiza el **comportamiento de sus clientes** con datos registrados hasta el año 2024 para:

- Construir un **perfil estadístico** de los clientes.
- Detectar **comportamientos atípicos** (outliers).
- Crear **segmentos de clientes** por edad y nivel de uso.
- Proponer **estrategias de retención** y **mejoras en los planes** ofrecidos.

## Datasets utilizados

| Archivo | Descripción |
|---|---|
| `plans.csv` | Información de los planes actuales: precio, minutos incluidos, GB incluidos y costo por extra. |
| `users_latam.csv` | Información de los clientes: edad, ciudad, fecha de registro, plan y churn. |
| `usage.csv` | Detalle del uso real de los servicios: llamadas y mensajes (tipo, fecha, duración, longitud). |

> Los archivos se leen desde la ruta `/datasets/`.

## Etapas del análisis

1. **Carga y exploración:** lectura de los tres datasets, revisión de estructura, tipos de datos y dimensiones.
2. **Calidad de datos:** detección de valores nulos, sentinels (`-999` en `age`, `"?"` en `city`) y fechas fuera de rango.
3. **Limpieza:**
   - `age`: el sentinel -999 se reemplaza por la mediana de las edades válidas.
   - `city`: `"?"` se convierte en nulo.
   - `reg_date`: las fechas futuras (posteriores a 2024) se marcan como nulas.
   - `duration` y `length`: se confirma que sus nulos son MAR (dependen de `type`) y se dejan como nulos.
4. **Resumen por usuario:** se agrega `usage` por `user_id` (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) y se une con `users`.
5. **Visualización y outliers:** 
   - `grupo_uso`: Bajo uso, Uso medio, Alto uso.
   - `grupo_edad`: Joven, Adulto, Adulto Mayor.
7. **Insight ejecutivo:** conclusiones y recomendaciones para el negocio.


## Guía breve de reproducción

1. Clona o descarga este repositorio.
2. Coloca `plans.csv`, `users_latam.csv` y `usage.csv` en la ruta `/datasets/` (o cambia las rutas en la celda de carga de datos).
3. Instala las librerías: `pandas`, `numpy`, `seaborn`, `matplotlib`.
4. Ejecuta el notebook de arriba hacia abajo, sin saltarte celdas, porque cada paso depende de la limpieza anterior.
5. Revisa las salidas y los insights de cada sección.

## Tecnologías

Python · pandas · NumPy · seaborn · matplotlib

## Autor

Juan Antonio Iztetzi Conde 
