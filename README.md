<!-- This is a readme for the course of Fundamentals of Data Science course in UPC>
<!-- PROJECT LOGO -->
<div align="center">
    <img src="https://lh3.googleusercontent.com/cZekUlhBmFloSVLC_i-5D4UeYH0Wzu2UwchEv0jSWVdzmRZVsmvk8XSaRrzvdTj2r-M=w300" alt="Logo",align="center">
    
  <h1 align="center">Universidad Peruana de Ciencias Aplicadas - UPC</h1>
  <p align="center">
    <strong>CC216 - Fundamentos de Data Science</strong>
    <br>
    <strong>Trabajo Final - Grupo 2</strong>
    <br>
    Sección - CC52
    <br>
    <strong>Profesora: MANRIQUE TUNQUE, NERIDA ISABEL</strong>
    <br>
  </p>
  <p align="left">
    <strong>Integrantes :</strong>
    <br>
    <strong>Alcides Rommel Charapaqui Reluz &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;u202021294</strong>
    <br>
    <strong>Alonso Jesús Ulloa Vizquerra&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;u20161d217</strong>
    <br>
    <strong>Sebastian Aaron Guevara Dominguez&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;U20181h207</strong>
    <br>
    <strong>Daniel Ulises Barrionuevo Gutierrez &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;u201922128</strong>
  </p>
</div>

<center><h1>Proyecto - Bike Buyers</h1></center>

# Tabla de Contenidos

1. [Introducción](#data1)
2. [Objetivos](#data2)

    2.1. [Objetivos del Proyecto](#data21)

    2.2. [Objetivos Específicos](#data22)
3. [Miembros del Grupo y Roles](#data3)
4. [Conclusiones del Proyecto](#data4)
5. [Licencia de Uso](#data5)
<!-- REVISIONES-->
<!-- revisado hasta antes de aqui 1 -->
<!-- revisado indexes and subtitles -->
<!--  -->
## 1. Introducción <a name="data1"></a>
*Descripción del dataset. ¿Por qué es importante y qué pregunta/problema pretende responder?*

El dataset utilizado es ["**Bike_Buyers**" de Kagle](https://www.kaggle.com/datasets/heeraldedhia/bike-buyers). 
<center>Figura 1: Bike Buyers</center>
<p></p>
Las variables dadas y su descripción nos dan a conocer el caso de estudio en el cual estamos trabajando, un cliente el cual es vendedor de bicicletas y desea más información acerca de las ventas y los clientes potenciales. 
Para el vendedor de bicicletas es crucial saber que tipo de personas son potenciales compradores y/o para que otro sector puede dirigir las ventas. Para esto ser posible, los datos obtenidos deben ser revisados, pre-procesados y finalmente ser utilizados para lograr una conclusión la cual deberá ser entregada al vendedor.

```R
# Objetivo: Asegurar que estamos trabajando con el formato en ingles separado por comas
L <- readLines("bike_buyers.csv", n = 1)
if (grepl(",", L)) print("File has an English format")
```

    [1] "File has an English format"



```R
# Como estamos trabajando con ficheros separados por commas, vamos a mirar un poco de datos
df <- read.csv("bike_buyers.csv")
head(df)

# Mirando los nombres de columnas del dataframe y los tipos de variables y informacion adicional
print(paste("We are evaluating", nrow(df), "rows of code"))
print("Column's names: ")
colnames(df)
sapply(df,class)
str(df)
summary(df)
```


|index|ID|Marital Status|Gender|Income|Children|Education|Occupation|Home Owner|Cars|Commute Distance|Region|Age|Purchased Bike|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|12496|Married|Female|40000\.0|1\.0|Bachelors|Skilled Manual|Yes|0\.0|0-1 Miles|Europe|42\.0|No|
|1|24107|Married|Male|30000\.0|3\.0|Partial College|Clerical|Yes|1\.0|0-1 Miles|Europe|43\.0|No|
|2|14177|Married|Male|80000\.0|5\.0|Partial College|Professional|No|2\.0|2-5 Miles|Europe|60\.0|No|
|3|24381|Single|NaN|70000\.0|0\.0|Bachelors|Professional|Yes|1\.0|5-10 Miles|Pacific|41\.0|Yes|
|4|25597|Single|Male|30000\.0|0\.0|Bachelors|Clerical|No|0\.0|0-1 Miles|Europe|36\.0|Yes|



    [1] "We are evaluating 1000rows of code"
    [1] "Column's names: "

<ol class=list-inline>
	<li>'Id'</li>
	<li>'Marital Status'</li>
	<li>'Gender'</li>
	<li>'Income'</li>
	<li>'Children'</li>
	<li>'Education'</li>
	<li>'Occupation'</li>
	<li>'Home Owner'</li>
	<li>'Cars'</li>
	<li>'Commute Distance'</li>
	<li>'Region'</li>
	<li>'Age'</li>
	<li>'Purchased Bike'</li>
</ol>

<dl class=dl-horizontal>
	<dt>Id</dt>
		<dd>'integer'</dd>
	<dt>Marital Status</dt>
		<dd>'object'</dd>
	<dt>Gender</dt>
		<dd>'object'</dd>
	<dt>Income</dt>
		<dd>'float'</dd>
	<dt>Children</dt>
		<dd>'float'</dd>
	<dt>Education</dt>
		<dd>'object'</dd>
	<dt>Occupation</dt>
		<dd>'object'</dd>
	<dt>Home Owner</dt>
		<dd>'object'</dd>
	<dt>Cars</dt>
		<dd>'float'</dd>
	<dt>Commute Distance</dt>
		<dd>'object'</dd>
	<dt>Region</dt>
		<dd>'object'</dd>
	<dt>Age</dt>
		<dd>'float'</dd>
	<dt>Purchased Bike</dt>
		<dd>'object'</dd>
</dl>

## 2. Objetivos <a name="data2"></a>

<strong>Objetivos del proyecto:</strong> <a name="data21"></a>
    <br>
El objetivo principal del proyecto es comprender mejor el comportamiento de los clientes y optimizar la estrategia de ventas de la empresa de venta de bicicletas. Se busca obtener conocimiento sobre los patrones de compra, preferencias y características demográficas de los clientes.
	<br>
<strong>Objetivos de Data Science:</strong> <a name="data22"></a>
    <br>
Los objetivos de Data Science en este proyecto son aplicar técnicas y modelos de análisis de datos para extraer información significativa y responder a los objetivos del proyecto. Se utilizarán técnicas de minería de datos para identificar patrones, realizar predicciones y generar insights que ayuden en la toma de decisiones comerciales.
	<br>

## 3. Miembros del Grupo y Roles<a name="data3"></a>

<div align="center">

  <h1 align="center">Universidad Peruana de Ciencias Aplicadas - UPC</h1>
  <p align="center">
    <strong>CC216 - Fundamentos de Data Science</strong>
    <br>
    <strong>Trabajo Final - Grupo 2</strong>
    <br>
    Sección - CC52
    <br>
    <strong>Profesora: MANRIQUE TUNQUE, NERIDA ISABEL</strong>
    <br>
  </p>
  <p align="left">
    <strong>Integrantes :</strong>
    <br>
    <strong>Alcides Rommel Charapaqui Reluz &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Business Project Sponsor & Data Engineer</strong>
	<br>
	  Como Business Project Sponsor, mi función principal es liderar y respaldar proyectos empresariales desde su concepción hasta su implementación exitosa. Trabajo en estrecha colaboración con el equipo ejecutivo y los gerentes de proyecto para definir los alcances, plazos y recursos necesarios, asegurándome de que estén alineados con la estrategia y los objetivos de la empresa. Además, me encargo de comunicarme con stakeholders internos y externos, manteniéndolos informados y garantizando su participación activa. Para tener éxito en este rol, se requieren habilidades de liderazgo, gestión, resolución de problemas y toma de decisiones, junto con un sólido conocimiento del negocio y la industria.
En resumen, como Business Project Sponsor, mi objetivo es liderar proyectos empresariales, asegurando su alineación estratégica y su implementación exitosa a través de una gestión eficiente de recursos, comunicación efectiva y toma de decisiones informadas.
	<br>
	  <br>
    <strong>Sebastian Aaron Guevara Dominguez &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Data Scientist</strong>
	<br>
	 Como Data Science, me encargo de aplicar técnicas y algoritmos avanzados para extraer conocimiento y generar información a partir de los datos. Además, soy el responsable de desarrollar y aplicar modelos predictivos, algoritmos de aprendizaje automático y técnicas de minería de datos. También me encargaría de realizar la validación y evaluación del modelo, así como de interpretar los resultados obtenidos.
	<br>
    	<br>
   <strong>Alonso Jesús Ulloa Vizquerra&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Data Enginieer</strong>
	<br>
	  Como Data Engineer, mi principal responsabilidad es manejar los datos en su estado inicial, pero valiosos, para transformarlos, organizarlos y almacenarlos en bases de datos que sirven como fuente de información para otros roles en la organización. Mi objetivo es asegurar que los datos estén disponibles y listos para ser utilizados por otros profesionales en sus tareas.
Para desempeñar eficientemente mi trabajo, es crucial tener un conocimiento práctico y especializado en el campo de los datos, así como una comprensión de las nuevas necesidades de las empresas. Por ejemplo, es fundamental comprender cómo se modelan los datos y cómo funcionan las bases de datos SQL. Esta perspectiva me permite optimizar los procesos de almacenamiento y acceso a los datos, garantizando que estén estructurados de manera adecuada y sean fácilmente accesibles para su posterior análisis y uso..
	<br>
    	<br>
    <strong>Daniel Barrionuevo&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Data Analyst</strong>
	<br>
	  Como data analytics, mi deber fue examinar y recopilar los datos a través de herramientas y procedimientos especializados, para con los datos obtenidos juzgar y comparar el rendimiento de las estrategias ya existentes y así proponer nuevas soluciones o mejorar en los procesos de trabajo.
De igual manera se traducen los datos obtenidos en posibles cursos de acción para las empresas y sus respectivos departamentos y desarrollar las mejores estrategias.

  </p>
</div>






## 4. Conclusiones del Proyecto<a name="data4"></a>
<strong>Conclusiones:</strong>
   <br>
En conclusión, mediante la aplicación de la metodología CRISP-DM, este proyecto de análisis de datos ha permitido obtener información valiosa sobre el comportamiento de los clientes en relación a la compra de bicicletas. Con la participación de roles clave como el Business Project Sponsor, Data Science, Data Engineer y Data Analytics, se logró comprender los objetivos del negocio y los requisitos del proyecto. A través de la comprensión de los datos, la recolección y descripción de los mismos, y la visualización de los datos, se identificaron patrones y tendencias significativas en variables como ingresos, estado civil, nivel educativo, ocupación, propiedad de vivienda y edad. Estos hallazgos, obtenidos mediante la preparación de los datos y la construcción de modelos, han brindado insights importantes para la estrategia de ventas y respaldan la toma de decisiones comerciales más informadas.

  

En resumen, este proyecto ha demostrado el valor de la analítica de datos y la metodología CRISP-DM en la obtención de conocimientos para la toma de decisiones estratégicas en la empresa de venta de bicicletas.
	<br>

## 5. Licencia de Uso<a name="data5"></a>

### MIT LICENSE


<p>
 <a href="https://opensource.org/licenses/MIT">
  <img src="https://universoabiertoblog.files.wordpress.com/2017/06/mit_license_logo_by_excaliburzero-d9ur2lg.png" target="_blank"  style="height:222px;">
 </a>
</p>

Copyright (c) 2022 FrancoSimonini

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.