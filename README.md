# Mortalidad Infantil por Malformaciones Congénitas — Argentina 2024

Proyecto final del curso **Data Science I: Fundamentos para la Ciencia de Datos** (Coderhouse).
Análisis de microdatos públicos y modelo de clasificación aplicado a un problema de salud pública real.

## Descripción

Este proyecto analiza la mortalidad infantil por malformaciones congénitas en Argentina durante 2024, a partir de microdatos publicados por la **Dirección de Estadísticas e Información de Salud (DEIS)**. Combina análisis exploratorio, estadística descriptiva y un modelo de machine learning, con foco en identificar desigualdades territoriales y patrones clínicos en las causas de muerte infantil.

## Contexto

El Ministerio de Salud de la Nación identificó un aumento en la tasa de mortalidad infantil en el relevamiento demográfico de 2024 (+0,5 puntos respecto de 2023). Ante ese escenario, este trabajo profundiza en las causas de muerte en menores de un año, con foco en malformaciones congénitas —segunda causa de mortalidad infantil en el país— buscando generar información que oriente políticas públicas de salud, en particular la detección prenatal de cardiopatías congénitas y la reducción de brechas regionales.

## Objetivos

- Analizar la tasa de mortalidad infantil por provincia y región geográfica, para identificar desigualdades territoriales en el acceso a la salud materno-infantil.
- Desarrollar un modelo de clasificación que prediga si una defunción por malformación congénita corresponde a una **cardiopatía congénita (CIE-10 Q20–Q28)** o a otro tipo de malformación, en función de variables geográficas y etarias.

## Dataset

- **Fuente:** Dirección de Estadísticas e Información de Salud (DEIS), microdatos de defunciones 2024.
- **Alcance:** defunciones de menores de un año cuya causa básica corresponde a códigos CIE-10 del capítulo Q (malformaciones congénitas).
- **Tamaño tras limpieza:** 611 registros, equivalentes a 1.013 casos agregados.

## Metodología

1. Extracción y limpieza de microdatos (tratamiento de valores faltantes, normalización de variables geográficas y etarias).
2. Análisis exploratorio de datos (EDA) y estadística descriptiva por provincia, región y subgrupo etario.
3. Construcción de un modelo de clasificación binaria (cardiopatía congénita vs. otra malformación), evaluando **Regresión Logística** y **Random Forest**.

## Principales hallazgos

- **Brecha territorial marcada:** las regiones **NEA** (3,46 ‰) y **Cuyo** (2,85 ‰) presentan las tasas de mortalidad más altas por mil nacidos vivos, frente a Patagonia y la región Pampeana, con tasas significativamente más bajas.
- **Concentración etaria:** los casos se concentran en el período neonatal precoz.
- **Desempeño del modelo:** ambos modelos alcanzaron un desempeño perfecto (F1 = 1,00, AUC-ROC = 1,00).

  > **Nota metodológica:** este resultado no se interpreta como un modelo exitoso sin más — se identificó que responde a una **relación determinista entre la variable `CAUSA` y la variable objetivo** (la causa específica de defunción ya codifica, por definición, si se trata de una cardiopatía congénita). Este hallazgo se documenta como parte del análisis crítico del trabajo: un F1 perfecto es, en la mayoría de los casos reales, una señal de fuga de datos (*data leakage*) antes que de un buen modelo, y detectar esa causa fue parte central del ejercicio.

## Herramientas

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn`

## Estructura del repositorio

```
├── notebooks/
│   └── mortalidad_infantil_malformaciones_2024.ipynb
├── data/
│   └── (dataset procesado / diccionario de variables)
├── informe_final.pdf
└── README.md
```

## Autor

**Nicolás Martín** — [LinkedIn](https://linkedin.com/in/nicolás-m-65295a108)
