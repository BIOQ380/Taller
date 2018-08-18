# Laboratorio 02 - Alineamiento de secuencias ![](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/vertical-alignment.png?raw=true)

#### En este laboratorio vamos a diseñar partidores para PCR y vectores de clonación. Sigue las instrucciones y responde las preguntas, entre `[]` se indica el puntaje asignado a cada pregunta. Tus respuestas van a formar parte de la nota de taller 02.

#### Parte 1: Diseño de partidores

Comencemos por ir a NCBI y buscar un gen de interés.

- Ve a la base de datos [Gene de NCBI](http://www.ncbi.nlm.nih.gov/gene), escribe "SRY" en la barra de búsqueda y selecciona el gen SRY de _Homo sapiens_ (human).

![gene_sry](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/sry_gene.png?raw=true)

Los resultados deberían ser familiares, ya que, se trata de la base de datos que se usó en el primer taller.

Ya llegaste a la última parte de este laboratorio. Aquí vamos a seleccionar la secuencia del gen SRY de _Homo sapiens_ (human).

- Dirígete a "_NCBI Reference Sequences (RefSeq)_", y en "_mRNA and Protein(s)_" haz clic en el número de acceso de la secuencia del mRNA.
- Para este ejercicio necesitamos la **seceuncias codificante o Coding Sequence (CDS)**. Así que, en vez de hacer clic directamente en "FASTA", baja hasta el vínculo que dice **CDS**.
- Una pequeña ventana va a aparecer, haz clic en *FASTA* y copia esa secuencia en un editor de texto.

##### Perfecto! ya estás listo para diseñar partidores para amplificar el gen SRY. Para hacerlo vamos a utilizar dos herramientas:

##### 1. [Primer3](http://primer3.ut.ee) provee de varias secuencias como posibles partidores. Se utiliza online.

![primer3](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/primer3.png?raw=true)

##### 2. [AmplifX](http://jim.nord.univ-mrs.fr/recherche/equipe-t-brue/jullien-nicolas/programmation/amplifx/?lang=en) es un programa que nos permite hacer un PCR _in silico_, es decir, con AmplifX podemos simular la amplificación del gen probando los diferentes partidores propuestos por Primer3 y escoger la mejor combinación de _forward_ y _reverse_. Dirígete a la página y descarga AmplifX según tu sistema operativo e instala el programa.

![amplifx](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/amplifx.png?raw=true)

- Dirígete a la página de [Primer3](http://primer3.ut.ee) y copia y pega la secuencia codificantes del gen SRY de humano.
- Haz clic en `Pick Primers`.
- Al terminar, verás una página con los partidores propuestos. Tómate unos minutos para mirar los resultados.

![primer3_out](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/primer3_out.png?raw=true)

---

**16.** Agrega a tu informe una lista de los "_LEFT PRIMER_" y "_RIGHT PRIMER_" que obtuviste usando Primer3. [3]

---

- Ahora, vamos a usar AmplifX para hacer una amplificación _in silico_ con todos los partidores propuestos por Primer3.
- Abre AmplifX.
- Primero, en `Sequence` pega la secuencia codificante del gen SRY de _Homo sapiens_. También aumenta `Speed/Sensitivity` al máximo, y define la opción `Amplicon max length` a 1000 bp.

![amplifx1](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/amplifx1.png?raw=true)

- Segundo, en `Primer list` haz clic derecho, selecciona "Add a primer", y copia y pega la secuencia del primer partidor sugerido por Primer3. Repite éste paso para todos los partidores _forward_ y _reverse_ que obtuviste. Asegúrate de recordar cuáles son _forward_ y cuáles son _reverse_. En AmplifX puedes nombrar cada secuencia que vas agregando.
- Selecciona un partidor _forward_ y uno _reverse_ y haz clic en `Run PCR` para hacer tu primer PCR _in silico_.

![amplifx2](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/amplifx2.png?raw=true)

- Haz varios PCRs _in silico_ probando diferentes combinaciones de partidores.
- Si haces clic en el amplicón podrás ver información valiosa acerca de la amplificación. Además, al seleccionar un partidor, en la parte derecha del programa, podrás ver algunas carácteristicas como el porcentaje de GC. Usa esta información para escoger la mejor combinación de partidores para tu PCR.

![amplifx3](https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/amplifx3.png?raw=true)

---

**17.** Indica los partidores _forward_ y _reverse_ que escogiste y explica por qué son la mejor opción para amplificar el gen SRY de humano. [5]

**18.** ¿Cuál es el largo del amplicón? ¿Y la temperatura de _annealing_ sugerida? [3]
	
---

##### No olvides enviar tu informe de laboratorio al correo electrónico de la profesora ayudante: kat.mendez@uandresbello.edu. Tienes plazo hasta las 23:59 hrs del día lunes de la semana siguiente.
##### También, recuerda estudiar las lecturas designadas para la próxima semana. Puedes revisarlas en [Lecturas](https://github.com/BIOQ380/Lecturas) de la página del curso.

---

<p align="center">
<img width="50%" src="https://github.com/bioinf-biotec/labs_bioinf/blob/master/images/unab_cbib_horizontal.png?raw=true">
</p>
