# Taller 04 - Mapeo de _reads_ y búsqueda de variantes

##### En este taller vamos a explorar el mapeo de fragmentos de ADN en contra de una referencia para la búsqueda de variantes usando IGV.

Antes de comenzar, debemos conocer e instalar **IGV (_Integrative Genomics Viewer_)**, un software popular para la visualización de datos genómicos.

* Dirígete a la [página de IGV](http://software.broadinstitute.org/software/igv/home).

![igv_page](https://github.com/BIOQ380/Taller/blob/master/images/igv_page.png?raw=true)

* A continuación, en "**Downloads**" sigue las indicaciones para descargar e instalar IGV según tu sistema operativo.

![igv_downloads](https://github.com/BIOQ380/Taller/blob/master/images/igv_downloads.png?raw=true)

* Abre IGV.

![igv_inicio](https://github.com/BIOQ380/Taller/blob/master/images/igv_inicio.png?raw=true)

### 1. Genoma de referencia: hg19

Vamos a utilizar el genoma de referencia de humano versión hg19. En particular, vamos a trabajar con el cromosoma 20.

* En IGV, carga la referencia de humano disponible en el servidor de IGV:
	* Dirígete a `Genomes` -> `Load Genome from Server...`.
	* Selecciona el genoma de humano: "**Human (1kg, b37+decoy)**".

![load_genome](https://us.v-cdn.net/5019796/uploads/FileUpload/50/ea77178d2c4407230d0a0282777951.png)

![select_genome](https://github.com/BIOQ380/Taller/blob/master/images/select_genome.png?raw=true)

Usaremos la referencia "Human (1kg, b37+decoy)" porque tiene varias características pre-cargadas, como la anotación de los genes, lo que nos ayudará a darle contexto a las variantes que podamos identificar.

* Ya cargado el genoma de referencia, selecciona el **cromosoma 20** en el menú desplegable.

![select_chr](https://github.com/BIOQ380/Taller/blob/master/images/select_chr.png?raw=true)

![chr20_inicio](https://github.com/BIOQ380/Taller/blob/master/images/chr20_inicio.png?raw=true)

### 2. Mapeo de _reads_ contra la referencia

Ahora que tenemos el genoma de referencia cargado, podemos agregar un archivo de alineamiento que contenga la información del mapeo de _reads_ en contra de la referencia. Con esto, vamos a ser capaces de explorar las regiones del genoma humano representadas por las _reads_.

* Comencemos por cargar el archivo de alineamiento de la muestra NA12878:
	* Dirígete a `File` -> `Load from File...`.
	* Selecciona el archivo: **NA12878_wgs_20.bam**. Y haz clic en `Go`.

![load_file](https://us.v-cdn.net/5019796/uploads/FileUpload/10/48eeee26b88c6acafde8a76e8da4dd.png)

* Si el programa te consulta por un "_index file_", haz clic en `Go`.

![create_index](https://github.com/BIOQ380/Taller/blob/master/images/create_index.png?raw=true)

![bam_inicio](https://github.com/BIOQ380/Taller/blob/master/images/bam_inicio.png?raw=true)

Inicialmente, no podrás visualizar los datos. Necesitamos acercarnos a una región más pequeña para que IGV comience a mostrar las _reads_ mapeadas. Podemos hacer esto usando los controles de "acercamiento" (_zoom_) `-/+`, o escribiendo las coordenadas de alguna región de interés en el genoma.

* Vamos a acercarnos a un intervalo de interés dentro del genoma:
	* En la barra de búsqueda de coordenadas, escribe: "**20:10,002,371-10,002,546**" (mira la imagen a continuación).

![coords_enter](https://github.com/BIOQ380/Taller/blob/master/images/coords_enter.png?raw=true)

* Haz clic en `Go`. Deberías ver algo como en la imagen a continuación.

![coords_bam](https://github.com/BIOQ380/Taller/blob/master/images/coords_bam.png?raw=true)

Las barras verticales muestran la profundidad de cobertura, i.e. la cantidad de secuencias (_reads_) presentes en cada posición. Las barras horizontales representan a cada _read_ mapeado. Gris significa que esas bases son idénticas a la referencia (**_match_**), mientras que las de colores indican la presencia de una base diferente a la de la referencia (**_mismatch_**). También, podrás observar algunas _reads_ mapeando con inserciones y deleciones (**_insertions_** and **_deletions_**), indicados por símbolos `I` de color púrpura y "huecos" (interrumpiendo las _reads_), respectivamente.

### 3. Búsqueda de variantes

Perfecto! Ya tenemos el "mapa" de todas las _reads_ alineadas en contra del genoma de referencia. Entonces, ya podemos agregar la información acerca de las variantes identificadas a partir del mapeo.

* Vamos a cargar el archivo que contiene las variantes identificadas en la muestra NA12878 a partir del alineamiento en contra de la referencia:
	* Dirígete a `File` -> `Load from File...`.
	* Selecciona el archivo: **NA12878.vcf**. Y haz clic en `Go`.

![vcf_inicio](https://github.com/BIOQ380/Taller/blob/master/images/vcf_inicio.png?raw=true)

* Nuevamente, vamos a acercarnos a un intervalo de interés dentro del genoma:
	* En la barra de búsqueda de coordenadas, escribe: "**20:10,002,584-10,002,665**".
	* Haz clic en `Go`. Deberías ver algo como en la imagen a continuación.

![coords_vcf](https://github.com/BIOQ380/Taller/blob/master/images/coords_vcf.png?raw=true)



##### No olvides enviar tu informe de laboratorio al correo electrónico de la profesora ayudante: kat.mendez@uandresbello.edu. Tienes plazo hasta las 23:59 hrs del día lunes de la semana siguiente.

---

<p align="center">
<img width="50%" src="https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/unab_cbib_horizontal.png?raw=true">
</p>
