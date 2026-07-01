# NOTAS

## Fuentes consultadas

Durante el desarrollo del trabajo se consultaron distintas fuentes para comprender la terminología del béisbol, fundamentar la construcción de la variable respuesta y resolver aspectos técnicos relacionados con la implementación de los modelos.

## Bibliografía sobre béisbol

Las siguientes referencias se utilizaron para interpretar el significado de acciones como *swing*, *bunt* y *strike*, permitiendo establecer criterios consistentes para clasificar los distintos valores de la variable `description`. Además, se anexa el reglamento que sirvió como base para definir algunos otros casos.

- Baseball Almanac. *Baseball Dictionary: Swing*. Disponible en:  
  https://www.baseball-almanac.com/dictionary-term.php?term=swing

- Baseball Almanac. *Baseball Dictionary: Bunt*. Disponible en:  
  https://www.baseball-almanac.com/dictionary-term.php?term=bunt

- Baseball Almanac. *Baseball Dictionary: Strike*. Disponible en:  
  https://www.baseball-almanac.com/dictionary-term.php?term=strike

- Major League Baseball. *Official Baseball Rules 2025*. Disponible en:  
  https://mktg.mlbstatic.com/mlb/official-information/2025-official-baseball-rules.pdf

## Documentación técnica

Durante la construcción de los modelos también se consultó la documentación oficial de las principales bibliotecas utilizadas:

- scikit-learn: https://scikit-learn.org/stable/
- statsmodels: https://www.statsmodels.org/stable/


## Decisiones metodológicas

La variable respuesta `swing` se construyó a partir de la variable `description`, considerando como **swing** aquellos eventos que representan un intento voluntario del bateador por golpear la pelota. La clasificación de cada evento se realizó utilizando las definiciones y reglas oficiales del béisbol provistas por las fuentes citadas anteriormente.

Para el desarrollo del modelo predictivo se utilizaron las bibliotecas mencionadas en la sección de documentación técnica, consultando su documentación oficial para la implementación de los distintos métodos y algoritmos empleados.