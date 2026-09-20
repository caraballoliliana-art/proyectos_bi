# 📊 Sales Performance Dashboard (Power BI)

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power_Query-ETL-orange?style=for-the-badge)

## 📝 Descripción del Proyecto
Este proyecto consiste en el desarrollo de un Cuadro de Mando (Dashboard) interactivo en **Power BI** diseñado para analizar el rendimiento financiero, las ventas globales y la rentabilidad de una empresa manufacturera multinacional. 

El objetivo principal es transformar datos transaccionales brutos en insights estratégicos que permitan a los directores de la empresa identificar qué mercados, segmentos y productos están impulsando el crecimiento y cuáles presentan riesgos de pérdida.

---

## 📸 Capturas del Dashboard
![Financial Dashboard](./Dashboard_sales.png)

---

## 🛠️ Habilidades Técnicas Demostradas

* **Proceso ETL (Power Query):** * Limpieza y estandarización de nombres de columnas (eliminación de espacios en blanco redundantes).
  * Tratamiento de valores nulos e indeterminados en la categorización de bandas de descuento (`Discount Band`).
  * Optimización de tipos de datos para mejorar el rendimiento del modelo.
* **Modelado de Datos:**
  * Implementación de buenas prácticas mediante la creación de una **Tabla de Dimensiones de Calendario (`Dim_Calendar`)** nativa en DAX para análisis temporales continuos.
  * Separación lógica de medidas calculadas en una tabla dedicada (`_Medidas`).
* **Cálculos Avanzados (DAX):**
  * Creación de métricas clave de negocio utilizando funciones de agregación y lógicas financieras (`SUM`, `DIVIDE`).
  * Cálculo de márgenes de beneficio porcentuales dinámicos.
* **Diseño Visual y UI/UX:**
  * Estructuración del lienzo con un diseño corporativo limpio que prioriza la jerarquía visual.
  * Uso estratégico de colores (Alertas visuales y KPIs destacados en la parte superior).
  * Interactividad mediante segmentadores (*Slicers*) dinámicos por año, segmento y país.

---

## 📈 Métricas Clave y Fórmulas DAX Utilizadas

* **Ventas Totales:**
  ```dax
  Total Sales = SUM('Financial Sample'[Sales])
* **Beneficios totales:**
  Total Profit = SUM('Financial Sample'[Profit])
* **Margen de Beneficios:**
  Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
  * **Unidades vendidas:**
  Total Units Sold = SUM('Financial Sample'[Units Sold])
