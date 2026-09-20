# Prueba Técnica: Visualización de Datos Futbolísticos (Desafío Latam)

## 📋 Descripción del Problema
El Director Técnico (DT) de un importante equipo de una ciudad de España ha solicitado una herramienta interactiva para obtener un panorama detallada de los posibles equipos rivales en la próxima Champions League, así como para sondear nuevas contrataciones estratégicas para el club.

Para llevar a cabo este proyecto, se dispone de los siguientes conjuntos de datos:

* **`players.csv`**: Contiene la información detallada de los jugadores, su club actual y datos personales.
* **`clubs.csv`**: Listado maestro de equipos con datos de la liga en la que participan, entre otros.
* **`competitions.csv`**: Listado de ligas y competiciones.
* **`goal_games.csv`**: Listado de goles por partido y equipo.
* **`game_events.csv`**: Listado de goles por jugador.
* **`games.csv`**: Listado maestro de partidos.
* **`player_valuations.csv`**: Valoración del jugador en Euros en la fecha indicada.

---

## 🏗️ 1. Modelo de Datos y Relaciones

Se debe cargar la información y generar el modelo de datos considerando las siguientes relaciones estructurales:

| Tabla 1 | Tabla 2 | Relación (Campos) |
| :--- | :--- | :--- |
| `players.csv` | `clubs.csv` | `Current Club Id` = `Club Id` |
| `clubs.csv` | `competitions.csv` | `Domestic Competition Id` = `Competition Id` |
| `clubs.csv` | `goals_games.csv` | `Club Id` = `Club Id1` |
| `players.csv` | `game_events.csv` | `Player Id` = `Player Id` |
| `game_events.csv` | `games.csv` | `Game Id` = `Game Id` |
| `players.csv` | `player_valuations.csv` | `Player Id` = `Player Id` |

> ⚠️ **Filtro de Carga Crítico:** Al momento de cargar la tabla `game_events.csv`, se debe aplicar obligatoriamente un filtro de fuente de datos: **`Type` contiene "Goals"**.

---

## 🔍 2. Análisis Exploratorio de Datos (EDA)

Para responder a las primeras inquietudes del DT, se deben construir tablas o gráficos en Tableau que resuelvan las siguientes preguntas:

* **a. Países y Ligas:** ¿De qué países se tiene información? ¿Cómo se llama la liga de cada país y con cuántos equipos cuenta cada una?
    * *Tip:* Genera una tabla utilizando un recuento de los nombres de los clubs (`clubs.csv`) y extrae el nombre de la liga desde el campo `Name` en `competitions.csv`.
* **b. Top 10 Equipos Goleadores (2021):** ¿Cuáles fueron los 10 equipos más goleadores del año 2021?
    * *Tip:* Cuenta el número de filas en la tabla `game_events` para obtener los goles y filtra el año utilizando la variable de fecha correspondiente en `games.csv`.
* **c. Diferencia de Goles:** Genera una tabla que muestre la cantidad de partidos que han terminado con diferencias de goles específicas ($0, 1, 2, 3,\dots$). ¿Cuántos partidos han terminado con una diferencia de goles mayor que 5?
    * *Tip:* Es necesario crear un campo calculado para extraer el valor absoluto de la diferencia de goles.
* **d. Distribución de Goles:** Genera un gráfico que muestre visualmente la distribución de la diferencia de goles en los partidos.
* **e. Mapa de Procedencia:** Crea un mapa que refleje la procedencia mayoritaria de los jugadores en la base de datos utilizando el campo `Country of Birth` de `players.csv`. Utiliza elementos visuales (tamaño/color) que faciliten identificar de dónde provienen más o menos jugadores.

---

## 📊 3. Dashboard Interactivo de Rendimiento de Ligas

Desarrollo de una herramienta interactiva que permita al DT analizar el comportamiento de las diferentes ligas del mundo en cualquier año seleccionado, visualizando de forma ágil:

* ⚽ Equipos con mejor rendimiento ofensivo.
* 🛡️ Equipos con mejor rendimiento defensivo.
* 🏆 Equipos con mayor cantidad de victorias.
* 💰 Equipos con mayor valoración en el mercado.

### Indicaciones Técnicas para el Dashboard:
1.  **Definición de KPIs:** Establece claramente los KPIs a mostrar y su metodología de medición.
2.  **Buenas Prácticas:** Asegura diferentes niveles de agregación (global, por ligas, etc.), manteniendo coherencia de colores, leyendas claras, gráficos óptimos e interactividad fluida.
3.  **Tips de Variables:**
    * **Goles por equipo:** Usar la variable `Club Goals` de `goals_games.csv`.
    * **Resultado del partido:** Usar la variable `result` de `goals_games.csv`.
    * **Valoración del jugador (2021):** Usar la variable `Market Value in Eur` de `player_valuations.csv`.

---

## 📈 4. Dashboard de Scouting y Contrataciones

Herramienta analítica enfocada en la toma de decisiones para la incorporación de un **Arquero (Goalkeeper)** y un **Delantero (Attack)**.

### Restricciones y Políticas del Club:
* **Edad:** Entre 22 y 30 años (calculada a partir de `Date of Birth` en `players.csv`).
* **Presupuesto:** El valor de mercado promedio del jugador no puede superar los **€30.000.000**.

### Requisitos del Dashboard:
* **Análisis por Posición:** Define y muestra métricas clave diferenciadas según la posición (por ejemplo, recuento de goles para los delanteros utilizando `game_events.csv`).
* **Filtros Avanzados:** Inclusión obligatoria de filtros por Competición/Liga y selectores dinámicos (sliders) para mover los límites del precio del jugador u otros indicadores relevantes.
* **Criterio de Ordenación:** Implementa un orden lógico y estratégico que ayude directamente al DT a elegir la mejor opción de fichaje.

---

## 📐 Fórmulas DAX y Columnas Calculadas Reference

A continuación se detallan las expresiones DAX base sugeridas para el desarrollo del modelo:

```dax
Cantidad de equipos = DISTINCTCOUNT(clubs[club_id])

Goles del club = SUM(goals_games[club goals])

Total de Goles = COUNTROWS(game_events)

Valor de Mercado = SUM(player_valuations[market_value_in_eur])

Victorias = CALCULATE(COUNTROWS(goals_games), goals_games[result] = "win")

Rendimiento defensivo = CALCULATE(COUNTROWS(games), goals_games[result] = "loss")

Recuento de jugadores = DISTINCTCOUNT(players[player_code])# analisis-ventas-python
