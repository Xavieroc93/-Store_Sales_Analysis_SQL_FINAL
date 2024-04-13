

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

<h3>Cargando las bases de datos</h3>
<br>
<p>  df_itens_pedidos = pd.read_csv('https://raw.githubusercontent.com/ElProfeAlejo/Bootcamp_Databases/main/itens_pedidos.csv')

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/50e314e0-a2c3-4ba7-b9ce-9cd58be75666)

<p> df_pedidos = pd.read_csv('https://raw.githubusercontent.com/ElProfeAlejo/Bootcamp_Databases/main/pedidos.csv')

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/e236b252-ca59-4c77-bf70-0ab10e1ac915)

<p>df_productos = pd.read_csv('https://raw.githubusercontent.com/ElProfeAlejo/Bootcamp_Databases/main/productos.csv')

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/1f32c945-ead8-4793-8242-69a126194dc3)

<p> df_vendedores = pd.read_csv('https://raw.githubusercontent.com/ElProfeAlejo/Bootcamp_Databases/main/vendedores.csv')</p>

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/198e2636-a8f5-4354-ac73-2af5a590763e)

<h3>Tratamiento de datos</h3>

Después de convertir todo a un DataFrame se tuvo que tratar los datos:

1.- TRATAMIENTO df_itens_pedido
  > <p>No se identifican valores nulos
  > <p>No se identifican valores duplicados

2.-TRATAMIENTO df_pedidos
  > <p>No se identifican valores nulos
  > <p>No se identifican valores duplicados
  > <p>Se identifica que varia informaciòn se repite de la tabla df_pedidos, por lo cual se recomienda que la informacion sea anexada a una sola tabla
  
3.- TRATAMIENTO df_productos
  > <p> No se identifican valores duplicados
  > <p> Se identifican valores 'NAN' que representa datos faltantes en columna "PRODUCTO" Y "SKU", son los mismos datos de estas columna que representan este valor Null
  > <p> Los datos faltantes son los dos últimos productos registrados podrían indicar que hubo algún problema o falta en el proceso de registro de esos productos. Esto podría deberse a diversas razones, como errores en la entrada de datos, problemas técnicos durante el registro, o simplemente que esos productos no fueron registrados correctamente en la base de datos.
 > <p> Es importante investigar y corregir este tipo de problemas, ya que la integridad de los datos es fundamental para realizar análisis precisos y tomar decisiones informadas. Una posible acción a tomar sería revisar el proceso de registro de productos para identificar posibles fallos y asegurarse de que todos los productos sean registrados de manera adecuada en el futuro.

4.- TRATAMIENTO df_vendedores
  > <p>Se identifica un nombre vendedor "Unknonw"
  > <p>No se identifican valores duplicados
  Se cambia tipos de datos
  Se cambia tipos de datos

<h2>EDA: Análisis exploratorio de los datos</h2>

<h3>Estadística Descriptiva</h3>

<p>A partir de nuestro análisis exploratorio inicial, hemos obtenido perspectivas preliminares de los datos.</p>

<h3> ANALISIS EVOLUCION DE VENTAS </h3>
<p>Se observó que el pico más alto en las ventas ocurrió el 24/11/2019, influenciado por dos eventos significativos en Brasil:</p>

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/d33979c1-f51f-481c-8f37-be1475f2cf88)

  <p>1.- Impacto del Black Friday: Este evento atrae a consumidores a aprovecha
  <p>2.- Victoria del Flamengo: La coincidencia de esta fecha con la celebración de Flamengo por ganar el Brasileirão y la Copa Libertadores pudo contribuir un clima de euforia nacional.
<p> La sinergia entre las promociones de Black Friday y la celebración deportiva pudo haber creado un ambiente excepcionalmente propicio para el consumo, lo cual fue estratégicamente aprovechado por la empresa para maximizar ingresos, implementando campañas de marketing que resonaron con el sentimiento colectivo de celebración.

<h4>Tendencia Decreciente</h4>

<p> Los datos indican una tendencia decreciente en las ventas en varias fechas de enero de 2019, específicamente el 27, 14, 15, 10, 6, 7, 8, 21, 11 y 9. Este patrón puede atribuirse a factores estacionales y económicos comunes en este período:

<p> Finalización de la Temporada Navideña: Las ventas suelen disminuir tras el fin de las festividades de diciembre, ya que los consumidores reducen sus gastos después de un período de compras intensas.

<p> Inicio del Año Fiscal: El comienzo de enero marca a menudo el inicio del año fiscal en varios lugares, lo que puede llevar a un comportamiento conservador en el gasto mientras los individuos y familias establecen sus presupuestos para el nuevo año.

<p> Efecto de la Cuesta de Enero: Enero es conocido por ser un mes donde los consumidores enfrentan restricciones presupuestarias después de los gastos de fin de año, lo que se refleja en una reducción notable en las ventas minoristas.

<h4> Ventas por dia de la semama </h4>

<p> El análisis de las ventas por día de la semana revela que los jueves, sábados y viernes son los días con mayores ventas, lo cual sugiere una oportunidad para intensificar las campañas de marketing durante estos días para maximizar los ingresos. Por otro lado, los lunes y martes muestran las menores ventas, indicando la necesidad de mejorar las estrategias promocionales en estos días para incrementar las transacciones. Estos insights pueden guiar la planificación de promociones y ofertas específicas para atraer más clientes en los días de menor rendimiento.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/40373908-afa5-4fa1-94ee-ab617a6a1831)

<h4> Comparaciòn Anual Ventas </h4>

<p> Tras un analisis sobre el crecimiento de las ventas entre 2019 y 2020 muestra un aumento significativo del 78%, reflejando un notable desarrollo en el comercio durante ese período. Para el año 2021, las ventas representan solo un 8% en comparación con el año anterior, lo cual es razonable considerando que los datos disponibles solo cubren hasta el inicio del primer trimestre.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/bf1bd12e-d883-47c9-8d7b-c4b0e6d8e572)

<p> Para mantener y potenciar la tendencia positiva del crecimiento de ventas observado entre 2019 y 2020, es fundamental implementar estrategias basadas en un análisis profundo del comportamiento del consumidor y las tendencias del mercado.

  <p> Análisis Predictivo: Continuar utilizando datos para prever tendencias futuras y adaptar las estrategias de marketing y ventas de manera proactiva.

  <p>Optimización de la Experiencia del Cliente: Mejorar la experiencia de compra online y en tienda, asegurando que los procesos sean eficientes y centrados en el cliente.

  <p>Personalización: Utilizar la tecnología para ofrecer promociones personalizadas y recomendaciones de productos basadas en el historial de compra y preferencias del cliente.

  <p>Diversificación de Productos y Servicios: Expandir el catálogo de productos para explorar nuevas categorías que puedan atraer a diferentes segmentos de clientes.

  <p>Refuerzo de Campañas en Días Clave: Intensificar las campañas de marketing durante los días de mayor venta y diseñar promociones específicas para los días de menor venta para equilibrar la distribución de la demanda a lo largo de la semana.

  <p>Estas estrategias no solo ayudarán a mantener el crecimiento de las ventas, sino también a adaptarse mejor a los cambios del mercado y a las expectativas de los consumidores.

<h3>ANALISIS DEL VENDEDOR</h3>

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/60fc4fe8-45a8-45bb-9adc-caa6264c63f2)
![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/01be4d48-77c6-4376-995a-d4388fa07139)


Paulo Calanca fue el vendedor con mayores ventas acumuladas desde 2019 hasta 2021. Sin embargo, en 2020, su rendimiento disminuyó en comparación con el año anterior, y en el primer trimestre de 2021, tanto Ana Duarte como Daniel Siquiera lograron superar sus ventas, duplicando prácticamente sus propios números. Este cambio indica un notable aumento en la efectividad de ventas de Ana y Daniel, quienes han mejorado significativamente su desempeño, superando a Paulo en las ventas iniciales de 2021.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/3a417d2e-df58-473c-8d3d-962d14db75f7)
![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/00e9cafc-bc2a-43d2-9709-a1c093c01e81)


<h4> Posibles Razones para el Cambio en las Ventas </h4>

<p> Estrategias de Venta Diferentes: Los vendedores pueden estar utilizando métodos de venta distintos, algunos de los cuales pueden ser más efectivos bajo ciertas condiciones de mercado o con ciertos segmentos de clientes.

<p> Cambio en las Preferencias del Consumidor: Si los productos que ofrece Paulo ya no están alineados con las tendencias actuales o las necesidades del mercado, esto podría afectar sus ventas negativamente.

<p> Capacitación y Motivación: La falta de capacitación continua o desmotivación personal también puede impactar el rendimiento de un vendedor.

<p> Competencia Interna y Externa: Una competencia más agresiva tanto dentro del equipo de ventas como de competidores externos podría estar influyendo en las cifras.

<p> Portfolio de Productos: Quizás Ana y Daniel han diversificado los productos que ofrecen o se enfocan en artículos más demandados.

<p> Relaciones con los Clientes: Las habilidades de relación con el cliente de Ana y Daniel podrían ser superiores, generando repetición de negocios y referencias.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/e6b4a282-43d5-4137-a987-457ec11d6e64)

<h4>Recomendaciones para Mejorar las Ventas</h4>

<p> Capacitación en Ventas: Proporcionar a Paulo (y al resto del equipo) formación continua en técnicas de venta modernas y estrategias de negociación.

<p> Análisis de Datos de Ventas: Utilizar análisis de datos para identificar qué productos están vendiendo bien y ajustar el enfoque de ventas de Paulo. Incentivos y Motivación: Revisar el sistema de incentivos para asegurar que motiva adecuadamente a los vendedores.

<p> Mejora del Engagement del Cliente: Implementar herramientas o sistemas para mejorar la relación con los clientes, como CRM, para personalizar el servicio y mejorar la satisfacción del cliente.

<p> Feedback Regular: Establecer sesiones de retroalimentación con Paulo para entender sus desafíos y ajustar su enfoque de ventas según sea necesario.

<h3> PRODUCTOS </h3>

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/da6ec9b2-51fc-4e93-b363-f82727169284)

Distribución de Precios: Nuestra evaluación revela que la mayoría de los productos se ofrecen a precios accesibles, lo que indica una estrategia orientada hacia productos de menor costo y alta rotación. Esto podría ser un reflejo de una táctica deliberada para atraer a un segmento de mercado más amplio que busca opciones económicas.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/2a392ef1-dd83-4cb4-a221-e6ab6e9776cc)

Dominio de Marcas: Marcas como Zara, Mixed, Animale, Le Lis Blanc y Banana Republic dominan nuestro inventario en términos de volumen. Esta concentración de marcas conocidas podría ser explotada para fortalecer la imagen de marca y la lealtad del cliente mediante campañas de marketing específicas.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/4ee0e727-ad80-48e3-95c4-45ac78266458)

Condición de los Productos: La prevalencia de productos usados sugiere que nuestra tienda podría estar especializándose en el mercado de moda de segunda mano. Esta es una excelente oportunidad para posicionarnos como líderes en moda sostenible, a través de iniciativas de reciclaje y reutilización.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/6a557211-ff7a-4f8b-8751-86b02f773741)

Variabilidad de las Ventas: Las fluctuaciones en las ventas a lo largo del tiempo nos indican patrones estacionales, lo que puede ser crucial para planificar inventarios y promociones de manera más efectiva, alineando nuestras estrategias de marketing con los picos de demanda.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/622e7fd5-8244-49cc-a5dd-6e3497705f7f)
![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/902631cd-afd6-4a1e-a39b-f7a97c2f3d71)

Productos más Vendidos: Artículos como Bolsas Classica Roxa, Bolsa Intrecciato Caramelo y Sapato Cetim Pink son nuestros más vendidos, lo que subraya la importancia de mantener un buen stock de estos productos y centrar en ellos nuestras estrategias promocionales.

Análisis de Ventas y Costos por Ciudad

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/da35dd01-c9cc-4d3d-bdf6-468173a51801)

Distribución de Ventas: Nuestro análisis regional muestra que ciertas ciudades generan más ingresos que otras, lo que podría guiar la distribución de nuestros esfuerzos de marketing y optimización logística para capitalizar sobre estas áreas de alto rendimiento.

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/ac3ce94e-8c78-4fda-a7fe-59526f245be5)

Costo de Envío: La ciudad que tiene los mayores costo de envio es BR-AL, seguido de BR-PE y el mayor cotos de envio promedio es de BR-AP , BR-SC y BR-CE respectivamente, indicativo de quien genera mas costos por los volumenes de ventas a quien tiene un mayor costo pormedio que se tendra que revisar que lo ocasiona.

Recomendaciones Estratégicas

Optimización de Inventario: Priorizar el mantenimiento de un stock adecuado de los productos más vendidos y reevaluar la estrategia para aquellos con menor salida.

Estrategia de Precios Dinámicos: Implementar una estrategia de precios dinámicos que se adapte a las fluctuaciones del mercado y a eventos especiales, para maximizar los ingresos y la competitividad.

Marketing Personalizado: Desarrollar campañas de marketing enfocadas en las ciudades con mayores ventas y segmentar los esfuerzos promocionales para dirigirse a clientes específicos basados en sus patrones de compra.

Mejora Logística: Explorar opciones para reducir los costos de envío en las áreas más costosas y considerar la posibilidad de establecer almacenes en regiones estratégicas para mejorar los tiempos de entrega y reducir costos.


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



