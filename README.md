# ANÁLISIS DE DATOS EN LA TIENDA DE MODA ONLINE
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

> [!NOTE]
> Este proyecto está diseñado para realizar un análisis exhaustivo de los datos de una destacada tienda online en Brasil. Nuestro objetivo es responder a preguntas críticas de negocio, explorar profundamente el comportamiento del mercado y proporcionar insights estratégicos que apoyen el crecimiento y la optimización de la empresa. A través de un enfoque analítico riguroso, buscamos identificar oportunidades, optimizar operaciones y fortalecer la posición de la tienda en su sector competitivo. Este análisis no solo clarificará los desafíos actuales sino que también guiará las decisiones empresariales hacia resultados tangibles y mejoras sostenibles.

> [!CAUTION]
> Utilizar con fines educativos :octocat:

<h2>Problema del negocio</h2>

<table><tr><td> 
Ante la necesidad imperativa de prever y optimizar el gasto de los usuarios, una prominente empresa de comercio electrónico ha iniciado la búsqueda de soluciones innovadoras. En este contexto, nuestro equipo de científicos de datos ha sido convocado para llevar a cabo un análisis exhaustivo del comportamiento de ventas de la empresa. Este estudio no solo abarcará las operaciones de ventas generales, sino que también se extenderá al desempeño de los vendedores, la dinámica de los productos y las tendencias emergentes del mercado.

El objetivo es proporcionar un entendimiento profundo que permita a la empresa no solo anticipar las tendencias futuras, sino también implementar estrategias efectivas para maximizar los beneficios y mejorar la satisfacción del cliente. A través de este análisis, buscamos identificar patrones clave, detectar oportunidades de crecimiento y ofrecer recomendaciones basadas en datos que guíen a la empresa hacia decisiones estratégicas acertadas en su competitivo entorno de mercado.
</td></tr></table>

## Tratamiento de datos

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

<h3> ANALISIS DE PRODUCTOS </h3>

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


<h2>OPTIMIZACION DE TABLAS</h2>

Se ha observado que tanto la tabla df_itens_pedidos como la tabla df_pedidos comparten las columnas "pedido_id", "producto_id" y "total". Por lo tanto, surge la necesidad de simplificar estas tablas combinándolas en una sola tabla para mejorar la eficiencia y la gestión de los datos.

### Razones

Reducción de redundancia: Al combinar las tablas, evitamos duplicar información y reducimos la redundancia de datos. Esto conduce a un uso más eficiente del espacio de almacenamiento.
Facilita la gestión de datos: Al tener una sola tabla que contenga toda la información relevante, la gestión de datos se simplifica. Ya no es necesario realizar un seguimiento de múltiples tablas separadas para acceder a la información completa sobre los pedidos y los productos.
Mejora del rendimiento de consultas: Al reducir el número de tablas involucradas en una consulta, se puede mejorar el rendimiento del sistema, especialmente en bases de datos grandes. Las consultas tienden a ser más rápidas y eficientes cuando se accede a una sola tabla en lugar de múltiples tablas.

<h3>CREACION DE BASE DE DATOS EN MYSQL</h3>

<h4>1. Creación de la Tabla transacciones_pedidos </h4>
<p>Al almacenar tanto la fecha como la hora de cada transacción, obtienes una granularidad de datos que permite análisis más detallados, como identificar picos de venta por hora o evaluar la eficiencia de la logística y entrega. Esta precisión puede ser crucial para optimizar operaciones, entender el comportamiento del consumidor y tomar decisiones informadas

  > <p> id_recibo: Usar INT es adecuado para un identificador que no será la clave primaria
  > <p> producto_id NOT NULL y `vendedor_id`: Establecer como NOT NULL asegura que cada transacción debe estar asociada con un producto y un vendedor, manteniendola integridad de los datos.
  > <p> pedido_id INT PRIMARY KEY: Designado como PRIMARY KEY asegura unicidad y optimiza las búsquedas y relaciones. *cantidad,            
  > <p> valor_unitario, valor_total, costo_envio: Elegir DECIMAL(10,2) para valores monetarios proporciona precisión en cálculos financieros. *ciudad CHAR(5): Asumiendo que el código de ciudad siempre tiene 5 caracteres, CHAR(5) es eficiente en términos de almacenamiento, al tener longitud fija.</p>

<h4>2. Creación de la Tabla producto </h4>

  > <p> producto VARCHAR NOT NULL:. Asumir datos siempre presentes con NOT NULL es crucial para la integridad.
  > <p> precio DECIMAL(10,2) NOT NULL: Asegura precisión en el almacenamiento de precios.
  > <p> marca VARCHAR, condicion VARCHAR(28): Se recomienda especificar una longitud máxima para VARCHAR, basada en la longitud esperada más común para estos campos.

<h4>3. Creación de la Tabla vendedores</h4>

  >
  > <p> Nombre_vendedor VARCHAR(255) NOT NULL: VARCHAR(255) es un estándar de la industria para textos cortos, permitiendo flexibilidad en los nombres sin desperdiciar espacio.</p>
  >

<h3> Sugerimos una Base de datos de la siguiente manera:...</h3>

![image](https://github.com/Xavieroc93/-Store_Sales_Analysis_SQL_FINAL./assets/93497146/5c0591f9-632d-4aa1-9936-1dd5fc0556d9)


## RESPONDIENDO LAS PREGUNTAS 

### 1. ¿Cual es el Top 5 productos más vendidos históricamente?

![](https://i.imgur.com/g5DYZYe.png)

Históricamente el producto más vendido es el producto **Saia Midi
Cinto** con **549** ventas, a pesar de ello el que más ingresos generó
es el producto **Vestido Nude Reta** llegando a los **\$301K**

### 2. ¿Cual es la evolución histórica de las ingresos netos?

![](https://i.imgur.com/JzS2aZa.png)

El análisis de los ingresos netos históricos muestra un valor promedio
de **\$80 mil** de ingresos netos diarios desde el **2020**. También
podemos visualizar en el histórico que el día **24’Nov del
2019**, se reportó un ingreso neto de **\$280 mil** generando por la
venta de algunas marcas famosas.

### 3. ¿Cuáles son los ingresos netos por vendedor por año?

![](https://i.imgur.com/2ctUaAP.png)

Aunque **Paulo** es el mejor vendedor histórico ha mantenido un nivel de
ventas constante, ya que en el año 2020 fue el que menos vendió, sus
demás compañeros crecieron todos sus ingresos netos destacando a **Ana**
y **Daniel** sobrepasando los **\$5M** en el año en cuestión.

### 4. ¿Cuáles son las ciudades que proporcionan mayores ingresos netos?

![](https://i.imgur.com/bIvV7fg.png)

Destacando a las ciudades **Alagoas** y **Pernambuco**, con ingresos
netos superiores a **\$1.5M** durante todo el periodo histórico.
Mientras que **Mato Grosso do Sul** y **Acre** ocupan los últimos
lugares de la lista con ingresos netos inferiores a **\$1.2**, donde se
debe mejorar las acciones de ventas.

### 5. ¿Cómo son los márgenes de ganancia con los costos de envío entre los productos?

![](https://i.imgur.com/3bXM1NG.png)

Vemos que las carteras son las en total tienen mayor costo de envío, sin
embargo prácticamente como mandan en todos lados tienen un margen de
ganancias estándar del **20%**

# Conclusiones finales

* El analisis de la información precedentemente expuesta refleja importantes observaciones sobre la problemática de negocios y su evolución histórica que permite influir en la toma de decisiones estratégicas, con el objeto de impulsar el rendimiento.
* Se analizó la evolución histórica de las ventas por productos, el comportamiento por vendedor y la distribución geográfica a nivel nacional, lo que permite tener un conocimiento cabal del desarrollo histórico de las ventas y la representatividad asociada a cada vendedor y región del país.
* Con el objeto de impulsar el rendimiento, mejorar la eficiencia y reducir costos se sugiere implementar diversas campañas promocionales como la llevada a cabo el día 24/11 (Black Friday) distribuidas a lo largo del año. Capacitar o fortalecer las competencias de los vendedores menos eficientes. Eliminar la distribución de productos en las regiones menos rentables, fortalecer y sobreponderar la distribución logística en las regiones que representan menores costes de envío y mayor rentabilidad para la empresa.

> [!IMPORTANT]
> Esto fue un proyecto que participamos los miembros del canal del
> 
>[![](https://img.shields.io/youtube/channel/subscribers/UCuerQOTskuNkddcT738357g?style=for-the-badge&logo=youtube&label=ElProfeAlejo)](https://www.youtube.com/@ElProfeAlejo)
