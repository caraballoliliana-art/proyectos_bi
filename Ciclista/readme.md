# 🚴 Cyclistic Bike-Share: Estrategia de Conversión de Usuarios

Este proyecto analiza los patrones de comportamiento y uso de bicicletas del sistema de bicicletas compartidas de Chicago (**Cyclistic**), con el objetivo de diseñar estrategias de marketing basadas en datos para convertir a usuarios ocasionales (*casual riders*) en miembros anuales (*annual members*).

---

## 📌 1. Pregunta de Negocio (*Business Task*)
¿En qué se diferencian los patrones de uso de las bicicletas de Cyclistic entre los miembros anuales y los ciclistas ocasionales?

---

## 🔍 2. Principales Hallazgos (*Key Insights*)

* **Propósito del Viaje:**
  * **Miembros anuales:** Registran picos de uso marcados a las 8:00 hrs y 17:00 hrs de lunes a viernes. Sus viajes son más cortos y predecibles, reflejando desplazamientos laborales y escolares cotidianos.
  * **Ciclistas ocasionales:** Su volumen se concentra fuertemente en fines de semana (sábados y domingos) y en horas intermedias de la tarde. La duración promedio de sus viajes duplica a la de los miembros, lo que denota un uso primordialmente recreativo y turístico.
* **Preferencia de Equipamiento:** Los usuarios ocasionales muestran un alto porcentaje de uso de bicicletas eléctricas (*electric bikes*).
* **Concentración Geográfica:** Las estaciones más transitadas por usuarios ocasionales están ubicadas cerca de atracciones turísticas y parques de la costa del lago.

---

## 💡 3. Recomendaciones Estratégicas

1. **Campaña de Conversión de Fin de Semana:** Diseñar pases promocionales o descuentos en membresía anual que se activen mediante notificaciones *push* en la app exclusivamente los sábados y domingos.
2. **Marketing Geolocalizado en Puntos Turísticos:** Dirigir publicidad digital y física en el *Top 10 de Estaciones* costeras donde la afluencia de usuarios ocasionales es más densa.
3. **Paquete de Beneficios para Bicicletas Eléctricas:** Promocionar que la membresía anual elimina el cargo de desbloqueo o reduce la tarifa por minuto en modelos eléctricos, incentivando a los usuarios casuales recurrentes.

---

## 📁 Estructura del Repositorio

```text
├── data/
│   └── 202507-divvy-tripdata.csv   # Dataset (descarga externa)
├── notebooks/
│   └── cyclistic_analysis.ipynb    # Notebook con el análisis y visualizaciones
├── .gitignore                      # Configuración de exclusión de archivos
├── README.md                       # Documentación del proyecto
└── requirements.txt                # Librerías de Python requeridas