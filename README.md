

<h1>ANÁLISIS DE DATOS EN LA TIENDA DE MODA ONLINE-Store_Sales_Analysis_SQL</h1>

> [!NOTE]
> Este proyecto está diseñado para realizar un análisis exhaustivo de los datos de una destacada tienda online en Brasil. Nuestro objetivo es responder a preguntas críticas de negocio, explorar profundamente el comportamiento del mercado y proporcionar insights estratégicos que apoyen el crecimiento y la optimización de la empresa. A través de un enfoque analítico riguroso, buscamos identificar oportunidades, optimizar operaciones y fortalecer la posición de la tienda en su sector competitivo. Este análisis no solo clarificará los desafíos actuales sino que también guiará las decisiones empresariales hacia resultados tangibles y mejoras sostenibles.

Preguntas solictadas por la empresa a responder
1. ¿Cual es el Top 5 productos más vendidos históricamente?

2. ¿Cual es la evolución histórica de las ingresos netos?

3. ¿Cuáles son los ingresos netos por vendedor por año?

4. ¿Cuáles son las ciudades que proporcionan mayores ingresos netos?

5. ¿Existe otro insight que puedas proporcionar?
> . <br>

> [!CAUTION]
> Utilizar con fines educativos :octocat:

<h2>Problema del negocio</h2>

<table><tr><td> 
Ante la necesidad imperativa de prever y optimizar el gasto de los usuarios, una prominente empresa de comercio electrónico ha iniciado la búsqueda de soluciones innovadoras. En este contexto, nuestro equipo de científicos de datos ha sido convocado para llevar a cabo un análisis exhaustivo del comportamiento de ventas de la empresa. Este estudio no solo abarcará las operaciones de ventas generales, sino que también se extenderá al desempeño de los vendedores, la dinámica de los productos y las tendencias emergentes del mercado.

El objetivo es proporcionar un entendimiento profundo que permita a la empresa no solo anticipar las tendencias futuras, sino también implementar estrategias efectivas para maximizar los beneficios y mejorar la satisfacción del cliente. A través de este análisis, buscamos identificar patrones clave, detectar oportunidades de crecimiento y ofrecer recomendaciones basadas en datos que guíen a la empresa hacia decisiones estratégicas acertadas en su competitivo entorno de mercado.
</td></tr></table>

<h2>Stack de tecnologías</h2>

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

<h2>Configuración del ambiente</h2>

> [!IMPORTANT] 
> Se requiere importar las siguientes tecnologías librerías para poder trabajar con el proyecto
> ```
>import geobr
>import pandas as pd
>import numpy as np
>import matplotlib.pyplot as plt
>import seaborn as sns
>from matplotlib.patches import FancyBboxPatch
>from matplotlib.offsetbox import OffsetImage, AnnotationBbox
>import matplotlib.dates as mdates
>from matplotlib.ticker import FuncFormatter
>import matplotlib.ticker as ticker
>import geopandas as gpd
>from matplotlib.patheffects import withStroke
>import requests
>from io import BytesIO
>import matplotlib.pyplot as plt
>from matplotlib.offsetbox import OffsetImage, AnnotationBbox
>from io import BytesIO
>from sqlalchemy import create_engine, MetaData, Table, inspect, text
> ```

<h2>Obtención de datos</h2>

En este apartado desargaremos los datos con los cuales trabajaremos

<h3>Diccionarios/JSON -> Dataframes</h3>
Encontramos en los datos estructuras no muy amigables para el trabajo de un científico de datos pero a través de herramientas que nos provee Pandas supimos resolverlo
<br>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/c966a26e-1d77-4981-835a-a6d619626b59)

El resultado:

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/69af82ca-2243-4b1d-b807-a24ccdc2cccc)

<h3>Preprocesamiento general</h3>

Después de convertir todo a un DataFrame tuvimos que hacer un pre-procesamiento general que consistió en:
1. Eliminar columnas o variables que no aportaban información
2. Eliminar duplicados
3. Inputación de valores nulos
4. Transformación de estructuras de datos. Por ejemplo, String -> DateTime

<h2>EDA: Análisis exploratorio de los datos</h2>

<h3>Estadística Descriptiva</h3>

<p>A partir de nuestro análisis exploratorio inicial, hemos obtenido perspectivas preliminares de los datos.</p>

<h4>1. Número de visitas promedio (visitNumber) </h4>
<p>En promedio, los usuarios visitaron el sitio unas 3.67 veces. Sin embargo, existe una gran variabilidad, con una desviación estándar de 6.54 y un máximo de 58 visitas por usuario. Esto sugiere la presencia tanto de visitantes frecuentes como de aquellos que acuden ocasionalmente.</p>

<h4> 2. Uso de dispositivos móbiles (isMobile) </h4>
<p>Apenas el 9.75% de las visitas se efectuaron desde dispositivos móviles. Esta tendencia concuerda con el periodo analizado (2016-2017), época previa al auge de los pagos mediante plataformas digitales móviles por posible impacto del COVID.</p>

<h4>3. Interacciones por visitas </h4>
<p>Los usuarios interactuaron con el sitio un promedio de 36.48 veces por visita, visualizando un total de 28.62 páginas. Esto refleja que los usuarios que realizaron compras interactuaron significativamente con el sitio.</p>

<h4>4. Detección de nuevas visitas y potenciales nuevos consumidores</h4>
<p>Alrededor del 36.58% de las visitas correspondieron a nuevos usuarios, lo que proporciona una idea de la tasa de adquisición de nuevos clientes.</p>

<h4>5. Consumo promedio</h4>
<p>El gasto medio fue de aproximadamente 108,440,200 unidades y una desviacion de 145,673,700 unidades , presentando una alta variabilidad en las transacciones.</p>

<h4>6. Visitas de origen directo</h4>
<p>El 64.02% de las visitas fueron clasificadas como directas, indicando que una mayoría de los consumidores acceden al sitio sin interaccion en otras paginas de consulta de compras, lo cual puede reflejar un hábito de compra establecido en el comercio electrónico.</p>

<h4>7. Patrones temporales</h4>
<p>Los usuarios tienden a visitar el sitio más frecuentemente por la tarde, con un promedio de las 14:17 horas, y durante la mitad del año (junio y julio aproximadamente), con un mes promedio de 6.65.</p>

<h4>8. Recurrencia</h4>
<p>La frecuencia promedio de visitas es de aproximadamente 3.49 veces, lo que sugiere un nivel de lealtad y recurrencia entre los consumidores.</p>

<h3>Además...</h3>

<h4>Compoartamiento de los consumidores por día de la semana</h4>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/f653ffcb-68c9-4605-9634-6ace5488c66b)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/7f72cb21-33ec-49aa-9f27-a2edabf5402b)

<p>Esto indica que el martes y el miércoles son los días de mayor actividad en términos de número total de transacciones, destacándose como los momentos de la semana con mayor volumen de operaciones comerciales.

A pesar de que el martes tiene un alto volumen de transacciones, el análisis revela que el miércoles, seguido por el lunes, son los días donde se presentan más consumos. Esto sugiere que, aunque el martes sea significativo en cuanto a la cantidad de transacciones, el miércoles y el lunes son más relevantes en términos de la cantidad de consumos, reflejando posiblemente una mayor diversidad de compras realizadas o una mayor participación de consumidores activos en estos días.

Este análisis proporciona insights valiosos para la toma de decisiones en varios ámbitos del negocio:

Diseñar campañas de marketing dirigidas específicamente para los lunes y miércoles, con el objetivo de captar la atención de los consumidores en los días de mayor actividad de compra. Esto puede incluir ofertas especiales, descuentos, o promociones temáticas que incentiven aún más el consumo.

Asegurar que el inventario esté óptimamente preparado para satisfacer la demanda de los consumidores los lunes y miércoles, ajustando los niveles de stock basándose en los patrones de consumo observados.

Alinear los recursos de operaciones, logística, y soporte al cliente para asegurar una experiencia de compra fluida durante los picos de actividad, especialmente en los días identificados como de mayor consumo.</p>

<h4>Tendencia diaria</h4>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/1eb906a6-960e-46c7-828a-1f9afcbf5f67)

<p>La observación de picos altos de consumo en fechas específicas sugiere una relación significativa entre ciertos eventos o temporadas y el incremento en la actividad de compra. Estos periodos, como la Navidad, viernes Negro, son conocidos por impulsar el consumo debido a las promociones, descuentos y la naturaleza misma de las festividades, que fomentan el gasto.

Para capturar y analizar el impacto de estos eventos en el comportamiento de compra, se podría considerar la creación de variables indicadoras (variables dummy) en los análisis de datos.

Incorporar estas variables en modelos de análisis puede mejorar significativamente la capacidad para entender y predecir patrones de consumo, permitiendo a las empresas ajustar sus estrategias de marketing, inventario, y promociones de manera más efectiva. Además, el análisis de estas tendencias temporales puede ofrecer insights valiosos sobre el comportamiento del consumidor, ayudando a identificar oportunidades para introducir nuevos productos o servicios en momentos clave para maximizar el engagement y las ventas.</p>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/3e66ed68-8506-4cad-b712-fb5691ac9d50)

<h4>Comportamiento de los consumidores por hora del día</h4>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/cc0c6349-ee7f-487b-b23b-e1a03387eda6)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/88051b83-00de-479f-9f88-98b7c489d493)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/3fa5cd5d-da73-4f22-8c87-d5ccce453acf)

<p>La agrupación de las transacciones y consumos en cuatro horarios distintos es una estrategia eficaz para simplificar el análisis de datos y obtener insights más claros sobre los patrones de compra. Si las compras se presentan más en los horarios de la tarde, desde las 12:00 pm hasta las 24:00 pm, esto sugiere una tendencia clara en el comportamiento de los consumidores, preferentemente orientada hacia las actividades de compra en la segunda mitad del día.

Para este tipo de análisis, se divide el día en los siguientes cuatro intervalos:

Mañana (6:00 am - 12:00 pm): Este horario captura las actividades de compra temprano en el día, que pueden incluir compras impulsadas por necesidades de último minuto o la realización de pedidos planificados previamente.

Tarde (12:00 pm - 18:00 pm): Este intervalo cubre las horas después del mediodía hasta el comienzo de la noche. Este periodo parece ser crítico para las transacciones y consumos, posiblemente debido a las pausas para el almuerzo o el tiempo libre que las personas pueden tener para realizar compras en línea o físicas.

Noche (18:00 pm - 24:00 pm): Este periodo abarca las horas de la tarde hasta la medianoche. Las compras en este horario podrían estar influenciadas por la conclusión de la jornada laboral, compras de última hora, o actividades de ocio que incluyen compras en línea.

Madrugada (0:00 am - 6:00 am): Aunque este intervalo suele tener menos actividad de compra en comparación con otros momentos del día, es importante monitorearlo para identificar comportamientos de nicho o tendencias emergentes, como compras impulsivas nocturnas o compras internacionales en zonas horarias diferentes.</p>

<h3>Por otro lado...</h3>

<p>También analizamos otros patrones que aportarían información valiosa a la hora de tomar decisiones:</p>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/73308001-5264-4fbe-93c5-2d442947bfe3)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/1a81c4a5-a624-4138-8ab2-583f51196076)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/03adf97b-1727-4713-b065-c7d8b7431921)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/985672d5-5a52-400b-9339-a6c817e294a2)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/84f540fa-9be7-4662-987a-9717e6fee081)

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/7007816d-152a-4e96-acb8-bc95d15dc6ef)

<h3>Nuestra variable TARGET: transactionRevenue </h3>

<p>transactionRevenue: Nos indica cuánto gastó el usuario del ecommerce</p>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/c472c5a9-ed62-42ea-8c25-78ee3bc6228e)


<h2>Feature Engineering</h2>

<h2>Construcción de los modelos para la predicción</h2>

<p>Para la construcción de los modelos nos apoyamos en múltiples opciones para poder obtener lo mejor de cada algoritmo de Machine Learning</p>
  
  1. LinearRegression
  2. Random Forest Regression
  3. XGBoost
  4. LightGBM
  5. CatBoost
  6. Votación

<h2>Evaluación de los modelos</h2>

![image](https://github.com/pabloing93/consumer_spending/assets/32267303/f0a00d2c-7ec4-41b6-ba5e-81d4a98fe337)


![image](https://github.com/pabloing93/consumer_spending/assets/32267303/22287b64-6e72-436c-9166-8c39f46661a1)



