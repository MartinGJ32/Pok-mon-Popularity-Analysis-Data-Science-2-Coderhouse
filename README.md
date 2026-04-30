# ¿Qué hace popular a un Pokémon?

Este repositorio corresponde al proyecto final del curso **Data Science 2 (Coderhouse)**.

El objetivo es analizar qué variables influyen en la popularidad de los Pokémon mediante la construcción de un índice cuantitativo basado en datos reales, y luego entrenar modelos predictivos que estimen el interés esperado de un personaje a partir de sus atributos.

Para ello, se combinan:

- Datos estructurales del [dataset de Kaggle (rounakbanik)](https://www.kaggle.com/datasets/rounakbanik/pokemon)
- Información adicional obtenida desde la [PokeAPI](https://pokeapi.co/) (habilidades, movimientos, experiencia base)
- Visitas mensuales reales extraídas de la **Wikipedia Pageviews API (Wikimedia)** como variable objetivo de popularidad

El enfoque es exploratorio en su primera fase, y predictivo en la segunda, buscando identificar patrones, relaciones y factores determinantes de la popularidad.

---

## Contenido del repositorio

- Notebook en Google Colab (`.ipynb`) con el análisis exploratorio completo y el entrenamiento de modelos
- Visualizaciones y validación de hipótesis
- Archivos de caché generados durante la ejecución (`pokeapi_data.json`, `wiki_pageviews.json`, `pokemon_raw.csv`)

---

## Variable objetivo

La variable `popularity` es un **índice normalizado (0–100)** construido a partir del promedio mensual de visitas a la página de Wikipedia de cada Pokémon en los últimos 24 meses. Se eligió Wikipedia sobre Google Trends porque la API oficial de Wikimedia es estable, reproducible y no requiere API key ni proxies.

---

## Hipótesis evaluadas

| ID | Tipo | Hipótesis |
|---|---|---|
| **H1** | Correlación | Los Pokémon con mayor poder total de combate (`total_stats`) no necesariamente son más populares, ya que la popularidad depende más de factores identitarios que de utilidad competitiva. |
| **H2** | Agrupamiento | Los datos de popularidad pueden agruparse por tipo elemental, revelando que tipos como Fuego, Dragón y Psíquico concentran la mayor popularidad por su estética y narrativa. |
| **H3** | Correlación | Existe una correlación negativa entre el número de generación y la popularidad, confirmando un efecto nostalgia: a menor número de generación, mayor popularidad promedio. |
| **H4** | Clasificación | El estatus legendario (`is_legendary`) es uno de los factores con mayor capacidad discriminatoria para separar Pokémon de alta vs. baja popularidad. |

---

## Tecnologías utilizadas

- Python
- Pandas / NumPy
- Matplotlib / Seaborn
- SciPy
- Requests (PokeAPI + Wikipedia Pageviews API)
- Scikit-learn (preprocesamiento, modelos baseline, evaluación)
- Random Forest / XGBoost
- SHAP (interpretabilidad de modelos)

---

## Estado del proyecto

**Primera fase — Análisis Exploratorio de Datos (EDA):** completada. Incluye adquisición y consolidación de datos desde tres fuentes, limpieza, ingeniería de features y validación de las cuatro hipótesis planteadas.

**Segunda fase — Modelado predictivo:** completada. Se aborda el problema como regresión (predecir el índice 0–100) y como clasificación binaria (popular / no popular usando la mediana como umbral). Modelos entrenados: Regresión Lineal y Ridge (baselines), Random Forest y XGBoost. Evaluación con RMSE, R², Accuracy, F1 y ROC-AUC. Interpretabilidad con SHAP values.
