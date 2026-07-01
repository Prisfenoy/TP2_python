# TP2_PYTHON

## Descripción

Este repositorio contiene la resolución del Trabajo Práctico Nº2 de Programación en Python.

El objetivo del proyecto consiste en desarrollar un modelo de clasificación capaz de predecir la probabilidad de que un bateador realice un **swing** frente a un lanzamiento de béisbol, utilizando información proveniente del sistema Statcast.

El trabajo comprende todas las etapas de un proyecto de aprendizaje automático:

- análisis exploratorio de los datos;
- construcción de la variable respuesta;
- preprocesamiento de los datos;
- selección de variables;
- entrenamiento y comparación de distintos modelos;
- elección del modelo final y generación de predicciones.

---

# Estructura del repositorio

```text
TP2_PYTHON/
│
├── datos/
│   ├── temporada1_original.parquet
│   ├── temporada1.parquet
│   ├── temporada2_original.parquet
│   ├── temporada2.parquet
│   ├── train.parquet
│   ├── test.parquet
│   └── validacion.parquet
│
├── notebooks/
│   ├── 01_Análisis_descriptivo.ipynb
│   ├── 02_Construccion_variable_rta.ipynb
│   ├── 03_Preprocesamiento_de_datos.ipynb
│   ├── 04_Selección_de_variables.ipynb
│   ├── 05_Random_forest.ipynb
│   ├── 06_Modelo_regresion_logistica.ipynb
│   ├── 07_Comparación_de_modelos.ipynb
│   └── 08_Modelo_final.ipynb
│
├── .gitignore
├── .here
├── .python-version
├── main.py
├── pyproject.toml
├── uv.lock
├── README.md
└── NOTAS.md
```

---

# Datos

Los archivos de la carpeta `datos/` corresponden a las distintas etapas del proyecto.

| Archivo | Descripción |
|----------|-------------|
| `temporada1_original.parquet` | Conjunto de datos original utilizado para el análisis exploratorio. No presenta modificaciones respecto de la fuente original. |
| `temporada1.parquet` | Versión procesada de `temporada1_original.parquet`, utilizada para el entrenamiento y evaluación de los modelos. |
| `temporada2_original.parquet` | Conjunto de datos original sobre el cual se deben realizar las predicciones finales. No presenta modificaciones respecto de la fuente original. |
| `temporada2.parquet` | Versión procesada de `temporada2_original.parquet`, utilizada para aplicar el modelo final. |
| `train.parquet` | Subconjunto destinado al entrenamiento de los modelos. |
| `test.parquet` | Subconjunto reservado para la evaluación del desempeño del modelo seleccionado. |
| `validacion.parquet` | Archivo de salida que contiene las predicciones finales generadas sobre `temporada2.parquet` para su posterior entrega. |

Cada observación representa un lanzamiento de béisbol e incluye información relacionada con las características del lanzamiento, la ubicación de la pelota, el conteo previo, el bateador, el pitcher y otras variables utilizadas para construir el modelo predictivo.

---

# Notebooks

Las notebooks deben ejecutarse en el siguiente orden.

## 01 - Análisis descriptivo

Se realiza el análisis exploratorio del conjunto de datos mediante estadísticas descriptivas y visualizaciones.

Incluye:

- análisis univariado;
- análisis bivariado entre las variables explicativas;
- construcción de variables derivadas.

---

## 02 - Construcción de la variable respuesta

Se construye la variable binaria `swing` a partir de la variable original `description`.

Se define:

- `swing = 1`: el bateador intenta golpear el lanzamiento.
- `swing = 0`: el bateador no realiza un intento de swing.

---

## 03 - Preprocesamiento de datos

En esta notebook se realizan las tareas de preparación de los datos para el modelado:

- partición en entrenamiento y prueba (`train` y `test`);
- tratamiento de valores faltantes;
- tratamiento de valores atípicos.

---

## 04 - Selección de variables

Se evalúan distintos métodos de selección de variables con el objetivo de obtener un conjunto de predictores que permita construir modelos parsimoniosos sin perder capacidad predictiva.

Entre los métodos considerados se incluyen:

- análisis exploratorio de la relación entre la variable respuesta y las variables explicativas;
- LASSO.

---

## 05 - Random Forest

Se entrena un modelo de Random Forest utilizando los efectos principales seleccionados.

Se evalúa su desempeño mediante distintas métricas, entre ellas log-loss, curvas ROC, accuracy y otras métricas de clasificación. Además, se analiza la importancia de las variables.

---

## 06 - Regresión logística

Se ajusta un modelo de regresión logística utilizando las variables seleccionadas mediante LASSO. En este modelo se incluyen tanto los efectos principales como las interacciones.

Su desempeño se evalúa mediante métricas de clasificación y curvas ROC.

---

## 07 - Comparación de modelos

Se comparan los modelos desarrollados utilizando las siguientes métricas:

- Accuracy;
- Sensibilidad;
- Especificidad;
- Valor Predictivo Positivo (VPP);
- F1-score;
- AUC;
- Log-loss.

A partir de estos resultados se selecciona el modelo definitivo.

---

## 08 - Modelo final

En primer lugar, se realiza la imputación de los valores faltantes en `temporada1.parquet` y `temporada2.parquet`.

Posteriormente, se reentrena el modelo seleccionado utilizando todas las observaciones disponibles en `temporada1.parquet`.

Finalmente, se generan las predicciones correspondientes a `temporada2.parquet`.

---

# Reproducción del proyecto

El proyecto fue desarrollado utilizando **Python** y **uv** para la gestión del entorno y las dependencias.

## Clonar el repositorio

```bash
git clone <URL_DEL_REPOSITORIO>
cd TP2_PYTHON
```

## Crear el entorno e instalar las dependencias

```bash
uv venv
uv sync
```

## Ejecución

Para ejecutar las notebooks, seleccionar el **kernel de Python asociado a `uv`** y ejecutar los archivos en el orden indicado en la siguiente sección.

---

# Reproducción de `validacion.parquet`

Para reproducir el análisis completo y generar el archivo `datos/validacion.parquet`, las notebooks deben ejecutarse en el siguiente orden:

1. `01_Análisis_descriptivo.ipynb`
2. `02_Construccion_variable_rta.ipynb`
3. `03_Preprocesamiento_de_datos.ipynb`
4. `04_Selección_de_variables.ipynb`
5. `05_Random_forest.ipynb`
6. `06_Modelo_regresion_logistica.ipynb`
7. `07_Comparación_de_modelos.ipynb`
8. `08_Modelo_final.ipynb`

La última notebook realiza la imputación de los conjuntos procesados, reentrena el modelo Random Forest seleccionado utilizando `temporada1.parquet` y genera el archivo `datos/validacion.parquet`, que contiene las predicciones finales correspondientes a `temporada2.parquet`.

---

# Modelo seleccionado

Luego de comparar los distintos modelos desarrollados, se seleccionó **Random Forest** como modelo final por presentar el mejor desempeño sobre el conjunto de prueba.

En particular, obtuvo valores superiores a 0,90 en las principales métricas de clasificación y un **log-loss aproximado de 0,27**, lo que evidencia una buena capacidad predictiva y una adecuada calibración de las probabilidades estimadas.

---

# Documentación adicional

El archivo `NOTAS.md` contiene las fuentes bibliográficas y la documentación técnica consultadas durante el desarrollo del proyecto, incluyendo las referencias utilizadas para comprender las reglas del béisbol y fundamentar la construcción de la variable respuesta.