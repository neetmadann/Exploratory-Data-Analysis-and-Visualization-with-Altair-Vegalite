# Exploratory-Data-Analysis-and-Visualization-with-Altair-Vegalite
# 🌍 Global Development Metrics — EDA with Altair

This project explores key indicators of global development over time, using **Altair** and **Vega-Lite** for expressive, interactive visualizations. The data includes metrics such as fertility rate, life expectancy, population, child mortality, and GDP for countries across various world regions.

---

## 📁 Dataset Overview

| Column           | Description                                           |
|------------------|-------------------------------------------------------|
| `Country`        | Name of the country                                   |
| `Year`           | Year of observation                                   |
| `fertility`      | Average number of children per woman                  |
| `life`           | Life expectancy at birth (in years)                   |
| `population`     | Total population of the country                       |
| `child_mortality`| Child mortality rate (deaths per 1,000 live births)   |
| `gdp`            | GDP per capita (in USD)                               |
| `region`         | World region (e.g., South Asia, Europe & Central Asia)|

---

## 🎯 Objectives

- Perform **exploratory data analysis (EDA)** on global development indicators.
- Visualize temporal trends and regional comparisons.
- Enable interactivity with brushing and tooltips.
- Understand socio-economic progress across countries and regions.

## 📊 Visualizations with Altair

This project uses Altair's layered charting system to create **interactive line + point charts** for the following variables:

- `fertility`
- `life`
- `population`
- `child_mortality`
- `gdp`

Each chart:
- Shows trends over time by `region`.
- Includes tooltips for exploring specific data points.
- Supports brushing (click-drag to highlight a time range).
- Is dynamically generated via Python loops for scalability.

---

## 🛠 Example Code

```python
import altair as alt

# Example: Line + point chart for life expectancy
brush = alt.selection_interval()

chart = alt.Chart(grouped_df).mark_line().encode(
    x=alt.X('Year:Q', axis=alt.Axis(format='d')),
    y=alt.Y('life:Q', title='Life Expectancy'),
    color=alt.condition(brush, 'region:N', alt.value('lightgray')),
    tooltip=['Year:Q', 'life:Q', 'region:N']
).add_params(brush)
