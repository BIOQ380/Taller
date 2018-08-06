# Taller 01 - Homología

Dirígete a la página de **[NCBI Genome Workbench](https://www.ncbi.nlm.nih.gov/tools/gbench/)** y en **Downloads** haz clic en el link de tu sistema operativo para descargar e instalar **Genome Workbench** un software para analizar datos biológicos.

#### NCBI Genome Workbench - Operaciones Básicas

Ya teniendo el software funcionando, primero debemos familiarizarnos con la plataforma, para ello vamos a seguir uno de los tutoriales que son parte de la documentación de NCBI Genome Workbench. 

* Dirígete al tutorial **[Basic Operation](https://www.ncbi.nlm.nih.gov/tools/gbench/tutorial1/)**.
* Sigue las instrucciones de la parte **Step 3: Using Search** para buscar el gen "_superoxide dismutase_" en la base de datos pública de NCBI. Verás una lista de resultados de tu búsqueda.
* Luego, sigue con **Step 4: Search for Genes** para identificar el gen en humano: busca "_Homo sapiens_" en la columna "_Organism_", y "SOD1" en la columa "_Label_". Añade el gen a un nuevo proyecto para poder trabajar con él.
* Sigue con **Step 5: Viewing your data**. Ahora, "SOD1 [Homo sapiens]" aparece en tus proyectos. En **Projects**, haz clic derecho en **SOD1 [Homo sapiens] -> Open New View -> Graphical View**. Notarás que aparece una lista de accesos a varias "secuencias", todas muestran diferentes atributos del gen.

|comienza con|atributo|
|:-----------:|:------:|
|NC_ |secuencia referencia del cromosoma|
|NG_ |secuencia referencia con algún grado de curación|
|NM_ |secuencia referencia del ARN mensajero (mRNA)|
|NP_ |secuencia referencia de la proteína|

* Haz esto dos veces seleccionando **NC_** y **NG_**. Sigue con **Step 6: The Graphical View** y tómate unos minutos para explorar.
* **The Graphical View** anota los atributos de las secuencias usando diferentes colores:

|color|sifnificado|
|:---:|:---------:|
|barra verde|genes|
|barra azúl|transcritos (mRNAs)|
|barra roja|regiones codificantes (CDSs) o proteínas|

Para más detalles acerca de la nomenclatura de The Graphical View, puedes revisar el documento [Sequence Viewer legends](https://www.ncbi.nlm.nih.gov/tools/sviewer/legends/).

* Sigue con **Step 7: Navigating in the Graphical View** y **Step 8: Zoomed In Detail**. Prueba haciendo _zoom-in_ y _zoom-out_ en el visualizador, mientras más _zoom-in_ hagas podrás ver más características. Existen 2 "trucos" para hacer _zoom-in_ y _zoom-out_: (i) manteniendo la tecla `Z` y el clic derecho del _mouse_ presionados mientras mueves el _mouse_ arriba y abajo, (ii) mantener presionada la tecla `R` para seleccionar con el _mouse_ la región a la que quieres hacer _zoom_. Además, si posicionas el _mouse_ sobre una región de la secuencias (durante ~1s), aparecerá un recuadro amarillo con información sobre la secuencia en general y sobre la posición en específico que estás apuntando.

#### NCBI Genome Workbench - Búsquedas Usando BLAST

**[BLAST (Basic Local Alignment Search Tool)](https://blast.ncbi.nlm.nih.gov/Blast.cgi)** es una herramienta de búsqueda de similitud entre secuencias biológicas. Mediante un alineamiento local es capaz de encontrar regiones similares entre una secuencia problema y otras cientos/miles/millones de secuencias contenidas en una base de datos.

#### NCBI Genome Workbench - Alineamiento Múltiple
