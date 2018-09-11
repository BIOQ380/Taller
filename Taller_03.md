# Taller 03 - Filogenética Molecular

##### En este laboratorio vamos a utilizar el software BEAST (_Bayesian Evolutionary Analysis Sampling Trees_) para analizar secuencias y estimar un árbol filogenético.

## Corriendo <img width="50%" src="http://beast.community/images/beast-banner.png">

### Descarga e instala BEAST

Para usar BEAST, necesitamos tener [Java](https://go.java/index.html) instalado. Entonces, primero vamos a descargar e instalar Java, y luego BEAST.

##### Para Windows

* Para descargar la última versión de Java, haz clic [aquí](http://www.oracle.com/technetwork/java/javase/downloads/index.html). Una vez en la página, selecciona el link de descarga que dice "**JRE**" (_Java Runtime Environment_). Haz doble clic en el archivo que descargaste, para instalar JRE.

* Descarga BEAST desde el siguiente link: [BEAST v1.10.1 - Windows version](https://github.com/beast-dev/beast-mcmc/releases/download/v1.10.1/BEAST.v1.10.1.zip). Vas a obtener un archivo comprimido ZIP. Descomprime el archivo `BEAST.v1.10.1.zip` y tendrás acceso a varios archivos ejecutables para correr BEAST, BEAUti, LogCombiner, TreeAnnotator, y TreeStat (i.e. programas de BEAST).

* Finalmente, para que todas las funciones de BEAST corran sin problemas, necesitamos instalar la librería BEAGLE. Descarga BEAGLE v3.0.1 para Windows [aquí](https://github.com/beagle-dev/beagle-lib/releases/download/v3.0.1/BEAGLE.v3.0.1.msi). Haz doble clic en el archivo que descargaste, para instalar BEAGLE.

##### Para Mac OS X

* Para descargar la última versión de Java, haz clic [aquí](http://www.oracle.com/technetwork/java/javase/downloads/index.html). Una vez en la página, selecciona el link de descarga que dice "**JRE**" (_Java Runtime Environment_). Haz doble clic en el archivo que descargaste, para instalar JRE.

* Descarga BEAST desde el siguiente link: [BEAST v1.10.1 - Mac OS X](https://github.com/beast-dev/beast-mcmc/releases/download/v1.10.1/BEAST.v1.10.1.dmg). Haz doble clic en el archivo que descargaste, para instalar BEAST.

* Finalmente, para que todas las funciones de BEAST corran sin problemas, necesitamos instalar la librería BEAGLE. Descarga BEAGLE v3.0.2 para Mac OS [aquí](https://github.com/beagle-dev/beagle-lib/releases/download/v3.0.2/BEAGLE.v3.0.2.pkg). Haz doble clic en el archivo que descargaste, para instalar BEAGLE.

### Corriendo BEAUti

BEAUTi es una aplicación útil para diseñar tus análisis y generar el archivo de control (_BEAST XML file_), que necesitaremos más adelante.

* <img width="10%" src="http://beast.community/images/icons/beauti-icon.png"> Abre BEAUti haciendo doble clic en su icono. Verás una ventana como esta:

![BEAUti](http://beast.community/tutorials/first_tutorial/images/image1.png)

Lo primero que debemos hacer, es cargar datos.

### Cargando el archivo NEXUS

Lo primero es subir un alineamiento de nucleótidos. Vamos a trabajar con los datos ejemplo de BEAST, descarga el archivo `apes.nex` [aquí](https://github.com/BIOQ380/Taller/blob/master/data/apes.nex). Este archivo contiene un alineamiento de las secuencias tRNA mitocondriales de 6 especies de primates - incluyendo un _outgroup_ - El inicio del archivo se ve así:

    #NEXUS
    
    BEGIN DATA;
	    DIMENSIONS NTAX=6 NCHAR=768;
	    FORMAT MISSING=? GAP=- DATATYPE=DNA;
	MATRIX
	human      AGAAATATGTCTGATAAAAGAGTTACTTTGATAGAGTAAATAATAGGAGC...
	chimp      AGAAATATGTCTGATAAAAGAATTACTTTGATAGAGTAAATAATAGGAGT...
	bonobo     AGAAATATGTCTGATAAAAGAATTACTTTGATAGAGTAAATAATAGGAGT...
	gorilla    AGAAATATGTCTGATAAAAGAGTTACTTTGATAGAGTAAATAATAGAGGT...
	orangutan  AGAAATATGTCTGACAAAAGAGTTACTTTGATAGAGTAAAAAATAGAGGT...
	siamang    AGAAATACGTCTGACGAAAGAGTTACTTTGATAGAGTAAATAACAGGGGT...
	;
    END;

* Vamos a cargar el alineamiento en formato NEXUS. Dirígete a `File` y selecciona la opción `Import Data...`. También puedes agregar un archivo haciendo clic en `+` en la parte inferior izquierda de la ventana, o arrastrando el archivo hasta la ventana.

![apes.nex](http://beast.community/tutorials/first_tutorial/images/image2.png)

Haz doble clic sobre el alineamiento que cargaste para darle un vistazo.

![aln_viewer](http://beast.community/tutorials/first_tutorial/images/image3.png)

En la ventana superior de la ventana encontrarás varias pestañas:

![tabs](http://beast.community/tutorials/first_tutorial/images/image4.png)

Todas ellas contienen opciones de configuración, en general, deberías trabajar de izquierda a derecha. Aunque, no todas las pestañas serán relevantes para todos los análisis.

### Configurando los datos taxonómicos

* Dirígete a la pestaña `Tips`, verás una tabla con todas las taxa que se encuentran en el alineamiento.

Le llamamos "_tips_" a las puntas de los brazos en un árbol filogenético, éstas representan los organismos contemporáneos que estamos analizando. Este panel `Tips` nos permite asignar una fecha a cada taxa. Los _taxon dates_ o _tip dates_ son importantes solo en ciertos casos, por ejemplo, cuando analizamos muestras de virus que evolucionan rápidamente o de DNA aislado desde un fósil (_ancient DNA_).

* Para nuestro caso con los primates, estaríamos analizando un árbol que representa millones de años de evolución, por lo que las fechas de nuestras _tips_ se pueden definir en cero. Esta es la configuración por defecto, todas las taxa tienen fecha (_Date_) cero.

![tips](http://beast.community/tutorials/first_tutorial/images/image5.png)

* Dirígete a la pestaña `Sites`.

### Ajustando el modelo evolutivo

En `Sites` podemos ajustar el modelo de evolución molecular para las secuencias que hemos cargado. Las opciónes que aparecen en ésta pestaña dependen de si has cargado secuencias nucleotídicas o aminoacídicas. En nuestro caso, hemos cargado el archivo `apes.nex` que contiene secuencias nucleotídicas:

![sites](http://beast.community/tutorials/first_tutorial/images/image6.png)

El modelo evolutivo por defecto es [HKY](https://www.ncbi.nlm.nih.gov/pubmed/3934395). Vamos a usar este modelo.

Al seleccionar la opción `Partition into codon positions`, se asume que las secuencias han sido alineadas como codones (alineamiento de regiones codificantes). En nuestro caso, los datos corresponden a secuencias de tRNA mitocondrial, por lo que no usaremos ésta opción.

### Ajustando el modelo de reloj molecular

* Dirígete a la pestaña `Clock` para ajustar el modelo de reloj molecular (_molecular clock_) a utilizar.

A diferencia de varios otros softwares filogenéticos, BEAST usa modelos de reloj molecular de forma de que los árboles tengan una escala de tiempo (una raíz u origen y una dirección en el tiempo). El modelo más simple es el definido por defecto, "_Strict clock_", que asume que todos los brazos del árbol tienen la misma tasa de evolución. Otros modelos de reloj molecular más complejos relajan ésta suposición en varias formas, pero no vamos a profundizar en ello ahora.

* Deja la opción `Clock Type` como `Strict clock` y dirígete a la pestaña `Trees`.

### Ajustando el modelo de _tree prior_

El _tree prior_ se refiere al árbol de partida o árbol anterior. En la pestaña `Trees` puedes definir el modelo que va a dar origen al inicio al árbol, entre otras opciones.

![trees](http://beast.community/tutorials/first_tutorial/images/image8.png)

En `Tree Prior` se despliega un menú con varias opciones que están divididas en modelos "_Coalescent_" (coalescente) y "_Speciation_" (especiación). Los modelos _Coalescent_ están pensados para poblaciones, mientras que los modelos _Speciation_ están diseñados para datos a nivel de especies.

* En `Tree Prior`, selecciona el modelo `Speciation: Yule process`.

[_Yule process_](http://rstb.royalsocietypublishing.org/content/213/402-410/21) es el modelo más simple de especiación, donde se asume que cada linaje se ha especiado a una misma tasa fija.

En la mitad inferior de la ventana en la pestaña `Trees` podemos escoger cómo seleccionar un árbol de partida/inicio.

* En `Tree Model`, selecciona `Random starting tree`. Esta opción se refiere a que se generará un árbol de forma aleatoria para correr el análisis filogenético en BEAST.

### _Priors_

* Dirígete a la pestaña `Priors`.

![priors](http://beast.community/tutorials/first_tutorial/images/image9.png)

En esta pestaña podemos especificar los _priors_ para cada parámetro. Los _priors_ corresponden a información que sabemos a priori, es decir, información que conocemos previamente y que podría ayudar a una inferencia más correcta del árbol filogenético. Seleccionar _priors_ es uno de los aspectos más desafiantes en un análisis Bayesiano. Por esta razón, los desarrolladores del software BEAST han definido apropiadamente varios _priors_ por defecto. En nuestro caso, vamos a usar los _priors_ por defecto.

### Operadores MCMC

A continuación, vamos a mirar los operadores ("_operators_") para MCMC (_**M**arkov **C**hain **M**onte **C**arlo_).

* Dirígete a la pestaña `Operators`.

![operators](http://beast.community/tutorials/first_tutorial/images/image10.png)

Cada parámetro tiene uno o más operadores. Los operadores especifican cómo cierto parámetro va cambiando mientras corre el MCMC. En `Operators` se muestra una tabla con los parámetros, sus operadores y los ajustes para cierto operador. En la primera columna están los nombres de los parámetros. Por ejemplo, `kappa` que significa que el modelo HKY tiene el parámetro _kappa_ (sesgo por transición-transversión). La siguiente columna indica el tipo de operador que actúa sobre cada parámetro. Por ejemplo, el operador `scale` escala el parámetro arriba y abajo según una cierta proporción.

La siguiente columna `Tuning`, indica un valor de ajuste para el operador. Los operadores que no tienen un valor de ajuste, tienen un "n/a" anotado en esta columna. Este valor establece qué tan grande será el movimiento que hará el operador, lo que afectará la frecuencia con la que este cambio ocurra durante el MCMC, lo que afectará la eficiencia del análisis.

En la parte superior de la ventana, sobre la tabla, se encuentra la opción `Auto Optimize`. Si seleccionas esta opción, los valores de ajuste se definirán automáticamente mientras corre el MCMC con el fin de alcanzar la máxima eficiencia.

La siguiente columna, `Weight`, contiene valores que especifican la frecuencia con la que se aplica un operador. Por ejemplo, el parámetro _kappa_ tiene un valor (_weight_) bajo, por lo que su frecuencia de cambio es baja.

* Selecciona la opción `Auto Optimize`, para dejar los ajustes por defecto. Continúa con la siguiente pestaña.

### Ajustando las opciones de MCMC

La pestaña `MCMC` provee de opciones de ajuste para correr BEAST:

![mcmc](http://beast.community/tutorials/first_tutorial/images/image11.png)

Primero, tenemos la opción `Length of chain`, que representa el número de pasos que el MCMC hará en la cadena antes de terminar. Qué tan alto debería ser este valor, depende del tamaño de datos, la complejidad del modelo y la calidad de la respuesta requerida. El valor por defecto, 10,000,000, es completamente arbitrario y se debería ajustar según el tamaño de los datos. Para saber qué valor de largo de cadena (_length of chain_) es adecuado, se puede utilizar un valor arbitrario y luego analizar el resultado (_log file_ o archivo de registros) utilizando el programa [Tracer](http://tree.bio.ed.ac.uk/software/tracer/). El objetivo de establecer un valor de largo de la cadena es lograr alcanzar un tamaño efectivo de la muestra (Effective Sample Size [ESS]).

Las opciones siguientes son para indicar qué tan seguido se va a generar un reporte del proceso para monitorear su progreso, el cual se muestra en pantalla y se guarda en el _log file_ (o archivo de registros). Estos valores, deberían ser ajustado de acuerdo al largo de las cadenas. Tomar registros muy seguido, puede resultar en un alto número de archivos con poca información en cuanto a la precisión del análisis, Mientras que, al tomar pocos registros a través del tiempo, vamos a tener un _log file_ con poca información acerca de la distribución de los parámetros. Por ejemplo, para 10,000 registros del proceso el valor debería ser el largo de las cadenas / 10,000.

* Como los datos que estamos trabajando son pequeños, y para que el proceso corra rápido, vamos a ajustar el valor de `Length of chain` a 1,000,000. También, ajusta los valores de `Echo state to screen every` y `Log parameters every` a 100.

Las siguientes dos opciones, son para indicar el nombre de los archivos de salida del análisis (resultados).

### Generando el archivo BEAST XML

Ahora, podemos crear el archivo BEAST XML, que es el archivo de control para correr BEAST. Contiene todas las instrucciones y parámetros que hemos ajustado hasta ahora, usando BEAUti.

* Selecciona `Generate XML` y guarda el archivo indicando un nombre apropiado y con extensión `.xml`.

###### Entonces, estamos listos para correr BEAST!

### Corriendo BEAST

* <img width="10%" src="http://beast.community/images/icons/beast-icon.png"> Abre BEAST haciendo doble clic en su icono. Verás una ventana como esta:

![beast](http://beast.community/tutorials/first_tutorial/images/image12.png)

* Haz clic en `Choose File...`, selecciona el archivo XML que acabas de crear usando BEAUti, y haz clic en `Run`.

Para mayor información acerca de las otras opciones, puedes revisar la documentación de BEAST en su [página](http://beast.community/beast).

Después de presionar `Run`, BEAST va a leer el archivo XML, y va a correr el análisis. En la ventana, podrás ver información que va a apareciendo mientras corre el programa. Comienza con mostrar el título y los créditos:

                       BEAST v1.X, 2002-2102
       Bayesian Evolutionary Analysis Sampling Trees
                 Designed and developed by
    Alexei J. Drummond, Andrew Rambaut and Marc A. Suchard
                              
               Department of Computer Science
                   University of Auckland
                  alexei@cs.auckland.ac.nz
                              
             Institute of Evolutionary Biology
                  University of Edinburgh
                     a.rambaut@ed.ac.uk
                              
              David Geffen School of Medicine
           University of California, Los Angeles
                     msuchard@ucla.edu
                              
                Downloads, Help & Resources:
                 	http://beast.community
                              
    Source code distributed under the GNU Lesser General Public License:
          	  http://github.com/beast-dev/beast-mcmc

Luego, escribe algunos detalles acerca de los datos que cargamos y de los modelos especificados. Deberías ver lo mismo que seleccionaste usando BEAUti.

    Random number seed: 1500828054875
    
    Parsing XML file: apes.xml
      File encoding: UTF8
    Looking for plugins in /Users/rambaut/Projects/BEAST/plugins
    
    Read alignment: alignment
      Sequences = 6
          Sites = 768
       Datatype = nucleotide
    Site patterns 'patterns' created from positions 1-768 of alignment 'alignment'
      unique pattern count = 69
    
    Using Yule prior on tree
    
    Creating the tree model, 'treeModel'
      initial tree topology = ((((bonobo,human),orangutan),gorilla),(chimp,siamang))
      tree height = 102.55912280908296
    
    Using strict molecular clock model.
    
    Creating state frequencies model 'frequencies': Initial frequencies = {0.25, 0.25, 0.25, 0.25}
    
    Creating HKY substitution model. Initial kappa = 2.0
    
    Creating site rate model: 
      with initial relative rate = 1.0
    
    Using Multi-Partition Data Likelihood Delegate with BEAGLE 3 extensions
      Using BEAGLE resource 0: CPU
    with instance flags:  PRECISION_DOUBLE COMPUTATION_SYNCH EIGEN_REAL SCALING_MANUAL SCALERS_RAW VECTOR_SSE THREADING_NONE PROCESSOR_CPU FRAMEWORK_CPU
      Ignoring ambiguities in tree likelihood.
      With 1 partitions comprising 69 unique site patterns
      Using rescaling scheme : dynamic (rescaling every 100 evaluations, delay rescaling until first overflow)
    
    Using TreeDataLikelihood
    Optimization Schedule: default
    
    Likelihood computation is using an auto sizing thread pool.
    
    Creating the MCMC chain:
      chainLength=1000000
      autoOptimize=true
      autoOptimize delayed for 10000 steps

A continuación, se muestran las citas para BEAST, y para los modelos seleccionados. Esto, con el objetivo a de ayudarte a describir tu análisis, especificando y citando los modelos usados.

    Citations for this analysis: 
    
    FRAMEWORK
    BEAST primary citation:
	Drummond AJ, Suchard MA, Xie Dong, Rambaut A (2012) Bayesian phylogenetics with BEAUti and the BEAST 1.7. Mol Biol Evol. 29, 1969-1973. DOI:10.1093/molbev/mss075
    
    TREE DENSITY MODELS
    Gernhard 2008 Birth Death Tree Model:
	Gernhard T (2008) The conditioned reconstructed process. Journal of Theoretical Biology. 253, 769-778. DOI:10.1016/j.jtbi.2008.04.005
    
    SUBSTITUTION MODELS
    HKY nucleotide substitution model:
	Hasegawa M, Kishino H, Yano T (1985) Dating the human-ape splitting by a molecular clock of mitochondrial DNA. J. Mol. Evol.. 22, 160-174
	
Finalmente, BEAST escribe información acerca del proceso para mantenerte informado de qué está pasando. La primera columna es el "_state number_", en este caso incrementa por 10,000, es decir, entre cada línea, han ocurrido 10,000 operaciones.

Recuerda que BEAST también está guardando los resultados en el _log file_, junto con un archivo de extensión `.trees` que contiene todos los árboles registrados en cada _state_.

También, BEAST comenzará a reportar el número de horas por millón de _states_, lo que permite estimar cuanto tiempo demorará el análisis.

    # BEAST v1.X
    # Generated Sun Jul 23 17:42:37 BST 2017 [seed=1500828054875]
    state	Posterior   	Prior       	Likelihood  	rootAge     
    0	-6812.7534  	-481.7973   	-6330.9561  	102.559     	-
    10000	-2910.2955  	-246.4611   	-2663.8344  	13.7383     	-
    20000	-2082.7664  	-234.0125   	-1848.7539  	0.12112     	-
    30000	-2049.3031  	-230.0213   	-1819.2818  	5.84813E-2  	-
    40000	-2043.1005  	-226.3604   	-1816.7401  	6.21508E-2  	-
    50000	-2042.1593  	-226.1915   	-1815.9678  	5.79924E-2  	-
    .
    .
    .
    
Al finalizar, se muestra una tabla con todos los operadores, cuanto tiempo fue usado, y otros detalles.

    950000	-2044.0265  	-227.1010   	-1816.9255  	5.98269E-2  	11.27 hours/billion states
    960000	-2041.6364  	-225.0546   	-1816.5818  	5.58888E-2  	11.27 hours/billion states
    970000	-2046.3378  	-227.5622   	-1818.7756  	5.96169E-2  	11.27 hours/billion states
    980000	-2039.9261  	-226.1422   	-1813.7839  	5.96151E-2  	11.27 hours/billion states
    990000	-2047.3466  	-227.6691   	-1819.6775  	6.41662E-2  	11.27 hours/billion states
    1000000	-2040.3296  	-225.5095   	-1814.8201  	5.74639E-2  	11.27 hours/billion states
    
    Operator analysis
    Operator                                          Tuning   Count      Time     Time/Op  Pr(accept) 
    scale(kappa)                                      0.239   13605      621      0.05     0.2453      
    frequencies                                       0.105   13530      722      0.05     0.2398      
    subtreeSlide(treeModel)                           0.025   202546     5651     0.03     0.2313      
    Narrow Exchange(treeModel)                                203114     7020     0.03     0.0547      
    Wide Exchange(treeModel)                                  40112      623      0.02     0.0099      
    wilsonBalding(treeModel)                                  40753      848      0.02     0.0053      
    scale(treeModel.rootHeight)                       0.148   40635      1192     0.03     0.2406      
    uniform(nodeHeights(treeModel))                           404956     13096    0.03     0.385       
    scale(yule.birthRate)                             0.126   40749      305      0.01     0.2392      

    41.987 seconds
    

## Analizando resultados y construyendo un árbol filogenético ![](https://github.com/bioinf-biotec/labs_bioinf/raw/master/images/tree.png?raw=true)

En esta segunda parte, vamos a examinar los resultados del análisis usando el programa [Tracer](http://tree.bio.ed.ac.uk/software/tracer/), y vamos a construir un árbol consenso y a visualizarlo usando [FigTree](http://tree.bio.ed.ac.uk/software/figtree/).

* Descarga e instala Tracer [aquí](https://github.com/beast-dev/tracer/releases). Para Windows selecciona el archivo con extensión `.zip`, descomprime y encontrarás los ejecutables. Para Mac OS X seleccina el archivo con extensión `.dmg`, una vez descargado haz doble clic para instalar.

* Descarga FigTree [aquí](http://tree.bio.ed.ac.uk/software/figtree/). En la parte derecha de la página, encontrarás los links de descarga. Para Windows selecciona el archivo con extensión `.zip`, descomprime y encontrarás los ejecutables. Para Mac OS X seleccina el archivo con extensión `.dmg`, una vez descargado haz doble clic para instalar.

### Examinando los resultados usando Trace

* Abre Tracer y carga los archivos `.log` que generaste en el análisis usando BEAST. Dirígete a la pestaña `Trace`.

Verás una ventana como la siguiente:

![tracer](http://beast.community/tutorials/second_tutorial/images/tracer.png)

Tracer es un programa para examinar resultados de análisis realizado por BEAST. Básicamente, nos queremos asegurar de que el análisis fue robusto y suficiente para inferir un árbol filogenético que represente la historia evolutiva de nuestros datos. Por ejemplo, en la ventana vemos que los valores ESS para varios de los parámetros son suficientes para terminar el análisis. Bajos calores de ESS significa que ciertos parámetros no se estimaron correctamente.

### Construyendo un árbol MCC

No es posible examinar todos los árboles creados durante el análisis de las secuencias por BEAST. Entonces, vamos a crear un árbol consenso que resuma la distribución posterior. Podemos hacer esto construyendo un árbol MCC (_maximum clade credibilty_) usando el programa TreeAnnotator del software BEAST.

* Abre el programa TreeAnnotator.

Verás una ventana como la siguiente:

![treeannotator](http://beast.community/tutorials/second_tutorial/images/mcc_settings.png)

Generalmente, usamos el 10% del número total de iteraciones como el _burn-in_ para un análisis (se puede ver en Tracer, al inicio del gráfico). 

* Haz clic en `Choose File...` de `Input Tree File` y agrega en archivo `.trees` que generó BEAST anteriormente.

* En `Output File` selecciona la carpeta de destino y escribe el nombre para el archivo de salida (resultado) que va a contener el árbol.

![saveas](http://beast.community/tutorials/second_tutorial/images/mcc_output.png)

* Haz clic en `Run`

TreeAnnotator comenzará a construir el árbol MCC. El progreso se puede monitorear mirando la siguiente ventana:

![running](http://beast.community/tutorials/second_tutorial/images/mcc_window.png)

### Visualizando el árbol MCC en FigTree

Finalmente, vamos a visualizar el árbol MCC en FigTree. Este programa permite visualizar el árbol, además de información acerca de este producida por TreeAnnotator.

* Abre FigTree, dirígete a `File` y selecciona `Open...` para abrir el archivo que contiene el árbol que recién generaste con TreeAnnotator (`apes.mcc.tree`).

* Dirígete a la pestaña `Trees`, selecciona `Order Nodes` - `increasing`.

* Aumenta el tamaño de las letras que indican el nombre de cada especie. Dirígete a `Tip Labels` y aumenta el valor para `Font Size`.

![figtree](http://beast.community/tutorials/second_tutorial/images/figtree.png)

---

##### Para el informe de este taller, deben escribir paso a paso el análisis de secuencias usando BEAST, y luego calcular y visualizar el árbol usando TreeAnnotator y FigTree. También, adjuntar una captura de pantalla por cada paso, incluyendo el árbol filogenético.

##### No olvides enviar tu informe de laboratorio al correo electrónico de la profesora ayudante: kat.mendez@uandresbello.edu. Tienes plazo hasta las 23:59 hrs del día lunes de la semana siguiente.

---

<p align="center">
<img width="50%" src="https://github.com/BIOQ380/Syllabus/blob/master/images/unab_cbib_horizontal.png?raw=true">
</p>
