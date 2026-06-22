# TP2_PYTHON

## Descripción del proyecto

Este repositorio contiene la resolución del Trabajo Práctico Nº2 de Programación en Python.

El objetivo del trabajo es construir un modelo predictivo que permita estimar la probabilidad de que un bateador realice un swing frente a un determinado lanzamiento de baseball.

Para ello se utilizan datos provenientes de Statcast, donde cada observación representa un lanzamiento realizado durante un partido. A partir de estas observaciones se realiza un análisis exploratorio, se define la variable respuesta y posteriormente se desarrollan modelos para predecir la decisión del bateador.

---

## Datos utilizados

Los datos utilizados se encuentran dentro de la carpeta `datos/`:

- `temporada1.parquet`: conjunto utilizado para realizar el análisis exploratorio, construir la variable respuesta, entrenar y evaluar los modelos.
- `temporada2.parquet`: conjunto utilizado para generar las predicciones finales.

Cada registro corresponde a un lanzamiento e incluye información relacionada con:

- características del pitcheo:
    - velocidad de liberación (`release_speed`)
    - tipo de lanzamiento (`pitch_type`)
    - movimiento horizontal y vertical (`pfx_x`, `pfx_z`)
    - ubicación del lanzamiento (`plate_x`, `plate_z`)

- identificadores del jugador
    - bateador (`batter`)
    - pitcher (`pitcher`)

- características del enfrentamiento:
    - lado del bateador (`stand`)
    - mano del pitcher (`p_throws`)
    - cuenta previa al lanzamiento (`balls`, `strikes`)

---

## Estructura del repositorio
TP2_PYTHON/
│
├── datos/
│   ├── .gitkeep
│   ├── temporada1.parquet
│   └── temporada2.parquet
│
├── .gitignore
├── .here
│
├── Análisis_descriptivo.ipynb
├── Construccion_variable_respuesta.ipynb
│
└── README.md


---

## Notebooks

### Construccion_variable_rta.ipynb

En esta notebook se analiza la variable original `description` y se construye la variable respuesta binaria `swing`.

Se define:

- `swing = 1`: cuando existe evidencia de un intento del bateador sobre el lanzamiento.
- `swing = 0`: cuando no se observa una acción voluntaria del bateador.

La clasificación se realiza utilizando definiciones del dominio de baseball y reglas oficiales de MLB.

---

### Análisis_descriptivo.ipynb

En esta notebook se realiza la exploración inicial del conjunto de datos con el objetivo de comprender las características de los lanzamientos y detectar patrones relevantes para la predicción del swing.

Incluye:

- Análisis univariado de las variables cuantitativas y cualitativas, evaluando sus distribuciones, valores faltantes y cualquier patrón relevante para el problema.
- Análisis bivariado entre variables de interés, con el fin de identificar relaciones, asociaciones y comportamientos que puedan aportar información al problema predictivo.
- Identificación de variables potencialmente relevantes y propuesta de transformaciones o nuevas características que puedan incorporarse en los modelos.

---

## Reproducción del análisis

Para ejecutar las notebooks es necesario instalar previamente las dependencias utilizadas en el proyecto.

### Windows

1. Crear un ambiente virtual:

```bash
python -m venv .venv
````

2. Activar el ambiente virtual:

```bash
.\.venv\Scripts\activate
```

3. Instalar las librerías necesarias:

```bash
python -m pip install 
```

### Linux

1. Crear un ambiente virtual:

```bash
python3 -m venv .venv
```

2. Activar el ambiente virtual:

```bash
source .venv/bin/activate
```

3. Instalar las librerías necesarias:

```bash
python3 -m pip install 
```

---

## Ejecución de las notebooks

Las notebooks deben ejecutarse en el siguiente orden:

1. `Análisis_descriptivo.ipynb`

   Realiza la exploración inicial de los datos y analiza las características relevantes del conjunto.

2. `Construccion_variable_respuesta.ipynb`

   Construye la variable respuesta binaria `swing` a partir de la variable original `description`.

3. `Modelado.ipynb`

   Entrena y evalúa los modelos predictivos utilizando las variables seleccionadas a partir del análisis exploratorio.

---

## Modelado predictivo


---

## Resultados



