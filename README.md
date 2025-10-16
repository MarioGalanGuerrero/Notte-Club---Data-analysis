🧠 Análisis Exploratorio y Modelos — Salud Mental (Hito 3)

Este documento explica de manera sencilla y con lenguaje natural el código desarrollado para el análisis de datos hospitalarios sobre salud mental.
Se incluyen los pasos de limpieza, análisis exploratorio, ingeniería de variables y modelos predictivos.

1️⃣ Carga y exploración de datos

Primero cargamos el archivo Excel que contiene todos los registros hospitalarios.
Se identificaron las hojas del documento y se eligió la hoja enfermedadesMentalesDiagnostico.
Después se visualizó una muestra inicial para comprobar que las columnas y los tipos de datos eran correctos.

2️⃣ Normalización de columnas y limpieza básica

Los nombres de las columnas se pasaron a minúsculas y se reemplazaron los espacios por guiones bajos (_).
Esto facilita el manejo de los datos en Python.
Luego se detectaron columnas con fechas y se transformaron a formato datetime, para poder calcular edades o estancias.

3️⃣ Conversión de tipos y anonimización

Se recodificaron variables numéricas como sexo (1 = hombre, 2 = mujer) y se eliminaron datos personales como el nombre o el CIP.
Esto es importante tanto por protección de datos personales (LOPD/GDPR) como por consistencia estadística.

4️⃣ Creación de variables derivadas

A partir de las fechas se generaron nuevas variables:

Año y mes de ingreso

Edad al ingreso

Indicador de ingreso en UCI

Estas variables permiten analizar la evolución temporal y los factores que influyen en la gravedad del caso.

5️⃣ Análisis exploratorio

Distribución de sexos

Edad promedio

Estancia media

Diagnósticos más frecuentes

También se generaron gráficos de tendencia mensual de ingresos y de estancia media, para visualizar cambios a lo largo del tiempo.

6️⃣ Detección de reingresos

Una parte interesante fue calcular si un paciente volvía a ingresar en menos de 30 días.
Para esto se generó un identificador anónimo (hash) por paciente y se compararon las fechas de alta e ingreso consecutivas.
Esta métrica es muy útil como indicador de calidad asistencial.

7️⃣ Modelos predictivos

Se desarrollaron varios modelos usando Random Forest y Gradient Boosting:

🏥 Reingreso a 30 días → modelo de clasificación

⏱️ Duración de estancia → modelo de regresión

🚑 Ingreso en UCI → modelo de riesgo

Cada modelo utiliza un pipeline automático con:

Codificación One-Hot Encoder

Separación de variables numéricas y categóricas

Validación cruzada y métricas como AUC, F1 o R²

8️⃣ Clustering diagnóstico

Para buscar patrones clínicos, se construyó un modelo de agrupamiento (K-Means) a partir de los códigos CIE.
Los diagnósticos se transformaron en texto vectorizado con TF-IDF, generando clusters con perfiles clínicos similares.
Esto permitió identificar grupos de pacientes con características afines, como trastornos afectivos o psicóticos.

9️⃣ Reglas de asociación

Se aplicó el algoritmo Apriori para descubrir combinaciones frecuentes entre diagnósticos y procedimientos.
Estas reglas ofrecen insights sobre qué intervenciones se asocian a determinados trastornos mentales y permiten descubrir patrones clínicos no triviales.

🔟 Conclusión

El proyecto combina:

📊 Análisis descriptivo

🧩 Minería de datos

🤖 Modelos predictivos

Todo aplicado al contexto hospitalario de salud mental.

Los resultados permiten extraer conocimiento útil sobre:

-Los perfiles de los pacientes

-Los factores de reingreso

-Las variables clínicas más relevantes

El lenguaje y la metodología buscan un equilibrio entre rigor técnico y claridad comunicativa, como en un trabajo académico universitario.
