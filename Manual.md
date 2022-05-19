Análisis de microsatélites
================

  - [Diversidad genética](#diversidad-genética)
      - [Arlequin](#arlequin)
  - [Estructura genética](#estructura-genética)
      - [Arlequin](#arlequin-1)
      - [STRUCTURE](#structure)
  - [STRUCTURE HARVESTER](#structure-harvester)
  - [SPAGeDi](#spagedi)
  - [Network](#network)

## Diversidad genética


### Genalex

Una opción para el cálculo de estadísticos básicos de genética de poblaciones con datos de microsatélites es Genalex. Las funciones importantes de este programa son:

1. Permite hacer diferentes cálculos en un solo programa
2. Permite exportar los datos a diferentes formatos para poder utilizar otros programas

En este taller solo vamos a calcular un par de cosas pero en el [manual](programas/GenAlEx6.51b2/QuickStarttoGenAlEx6.5.pdf) pueden encontrar más información de sus funciones.

#### Formato de entrada

Busquen el archivo de nu_genalex.xls en su carpeta de archivos_entrada y observen el formato de entrada para utilizar GenAlEx

![](imagenes/Genalex/G0.jpg)

Los números en la primera fila representan el número de loci, número de individuos (total), número de poblaciones, numero de individuos por población, número de regiones y número de individuos por región.

La segunda fila indica los nombres de las poblaciones y las regiones.

Después sigue una matriz de indiviudos x loci en la que se observan los alelos para cada individuo.

#### Activar Genalex

Genalex se activa como un add-in en Excel. **(Opciones)>>Add-ins>>Manage>>Browse**

![](imagenes/Genalex/G1.jpg)
![](imagenes/Genalex/G2.jpg)
![](imagenes/Genalex/G3.jpg)
![](imagenes/Genalex/G4.jpg)

Seleccionar el archivo ejecutable de GenAlEx en la carpeta de programas. Si es exitoso debería aparecer una nueva pestaña en la barra de herramientas de Excel.

![](imagenes/Genalex/G5.jpg)

#### Análisis

En este ejemplo vamos a calcular la heterocigocidad observada y esperada para cada una de las poblaciones.

En la pestaña de análisis basados en frecuencias, seleccionamos la opción de frecuencias.

![](imagenes/Genalex/G6.jpg)

Aparece una ventana con la descripción de las poblaciones.

![](imagenes/Genalex/G7.jpg)

Seleccionamos los análisis a realizar y los corremos.

![](imagenes/Genalex/G8.jpg)

### Arlequin (diversidad)

    ## [Profile]
    ##      Title="cp_Qhum"
    ##      NbSamples=22
    ##      GenotypicData=0
    ##      GameticPhase=0
    ##      RecessiveData=0
    ##      DataType=MICROSAT
    ##      LocusSeparator=WHITESPACE
    ##      MissingData='?'
    ##      CompDistMatrix=1
    ## [Data]
    ##   [[Samples]]   #Data for 5Loci: cmcs2 cmcs14 cmcs7 cmcs6a cmcs3a
    ##      SampleName="viro"
    ##      SampleSize=10
    ##      SampleData=     {
    ##        qhu001     1  139 163 205 197 164
    ##        qhu002     1  139 163 205 197 164
    ##        qhu003     1  139 173 205 197 164
    ##        qhu004     1  139 173 205 197 164
    ##        qhu005     1  139 173 205 197 164
    ##        qhu006     1  139 173 205 197 164
    ##        qhu007     1  139 173 205 197 164
    ##        qhu008     1  139 173 205 197 164
    ##        qhu009     1  139 173 205 197 164
    ##        qhu010     1  141 177 207 199 166
    ##      }
    ##      SampleName="vile"
    ##      SampleSize=11
    ##      SampleData=     {
    ##        qhu011     1  139 173 205 197 164

Partes del archivo de entrada de Arlequin:

1.  Descripción de los datos (las más importantes se mencionan a
    continuación):

    1.  Título del proyecto
    2.  Número de poblaciones
    3.  Tipo de datos (haplotípicos o genotípicos)
    4.  Tipo de datos (microsatélites, secuencias, etc)
    5.  Caracter de separación entre loci
    6.  Caracter para datos faltantes

2.  Datos organizados por “población”

    1.  Nombre de la población
    2.  Número de individuos
    3.  Datos:

    <!-- end list -->

      - La primera columna contiene la etiqueta de cada individuo
      - La segunda la frecuencia del genotipo
      - Las columnas siguientes contienen los datos por cada locus

<p align="center">

<img width="600" src="imagenes/Arlequin_div/01.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Arlequin_div/02.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Arlequin_div/03.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Arlequin_div/04.jpg">

</p>

En la página 117 del manual de Arlequín viene una descripción de los
diferentes índices obtenidos de la opción de índices de diversidad
molecular:

*Standard diversity indices*

1.  **Gene diversity**
2.  **Expected heterozygosity per locus**
3.  **Number of usable loci**
4.  **Number of polymorphic sites (S)**
5.  **Allelic range (R)**
6.  **Garza-Williamson index (G-W)**

*Molecular indices*

1.  **Mean number of pairwise differences (π)**
2.  **Nucleotide diversity or average gene diversity over L loci**

[Descripciones del manual](pdf/Arlequin_diversidad.pdf)

## Estructura genética

### Arlequin

Una forma de evaluar la estructura genética es a través de un análisis
de varianza molecular (AMOVA). El objetivo de este análisis es poner a
prueba una hipótesis de estructra. Como resultado se obtiene el
porcentaje de variación que hay dentro de las poblaciones, entre las
poblaciones y entre grupos de poblaciones.

[Excoffier, 1992](pdf/excoffier_1992.pdf) Artículo donde se describe el
método.

<p align="center">

<img width="600" src="imagenes/Arlequin_str/01.jpg">

</p>

### STRUCTURE

Descripción general del manual de STRUCRURE:

*The program structure implements a model-based clustering method for
inferring population structure using genotype data consisting of
unlinked markers. Applications of the method include demonstrating the
presence of population structure, identifying distinct genetic
populations, assigning individuals to populations, and identifying
migrants and admixed individuals*

*Briefly, we assume a model in which there are K populations (where K
may be unknown), each of which is characterized by a set of allele
frequencies at each locus. Individuals in the sample are assigned
(probabilistically) to populations, or jointly to two or more
populations if their genotypes indicate that they are admixed. It is
assumed that within populations, the loci are at Hardy-Weinberg
equilibrium, and linkage equilibrium. Loosely speaking, individuals are
assigned to populations in such a way as to achieve this.*

    ## cmcs2 cmcs14 cmcs7 cmcs6a cmcs3a
    ## qhu001 1 0 139 197 163 164 205
    ## qhu002 1 0 139 197 163 164 205
    ## qhu003 1 0 139 197 173 164 205
    ## qhu004 1 0 139 197 173 164 205

De manera general el archivo de entrada se compone de una matriz que
almacena la información de los individuos en las filas y la información
de los loci en las columnas.

**Filas**: La primera fila tiene los nombres de los loci. El resto de
las filas corresponde a los individuos.

**Columnas**: La primera columna corresponde a la etiqueta que
identifica cada individuo. La segunda los sitios de muestreo de donde
vienen los individuos. La tercera sirve para indicar si se quieren usar
los sitios de muestreo como estructura de la cual parte el análisis.

Pasos para el análisis:

1.  Abrir un nuevo proyecto y definir sus características.

<p align="center">

<img width="600" src="imagenes/Structure/01.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/02.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/03.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/04.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/05.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/06.jpg">

</p>

2.  Definir parámetros del análisis. Dependiendo del objetivo y de los
    datos que se tengan se pueden escojer distintos parámetros. Algunas
    desiciones importantes:

<!-- end list -->

  - *Largo de la corrida*

El objetivo de STRUCTURE es estimar el coeficiente de ancestría de cada
individuo dados ciertos parámetros que nosotros damos al modelo: los
genotipos, el número de grupos genéticos (K) y la distribución de las
frecuencias alélicas en cada locus y en cada población. Esta última se
obtiene de muestrear de manera independiente una cierta distribución. En
teoría deberíamos poder encontrar una distribución de frecuencias tales
que las poblaciones estén en equilibrio Hardy-Weinberg y en equilibrio
de ligamiento. En general el cálculo de la probabilidad de los
coeficientes de ancestría dados los parámetros no se puede resolver. Sin
embargo, se puede estimar si exploramos diferentes opciones de los
parámetros y calculamos su probabilidad. Por esta razón es que tenemos
que asegurarnos de que la corrida es lo suficientemente larga como para
que explore muchas opciones.

Otro parámetro que tenemos que decidir además del largo total de la
corrida es el largo del periodo de “descarte” (Burn in). Este periodo se
refiere al número de cálculos que no vamos a utilizar antes de empezar a
registrar los resultados. Se utiliza para descartar el posible efecto
que la configuración inicial puede tener sobre el resultado final.

<p align="center">

<img width="600" src="imagenes/Structure/08.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/09.jpg">

</p>

  - *Tipo de modelo de ancestría*:

    1.  **Sin mezcla (no admixture):** En este modelo los individuos de
        asignan de manera discreta a una u otra población. Se parte de
        una probabilidad inicial para cada población es de 1/K. El
        resultado reporta la probabilidad posterior de que el individuo
        pertenenezca a la población a la que fue asignado.

    2.  **Con mezcla (admixture):** Los individuos pueden tener
        ancestría mezclada. Se modela diciendo que el individuo “i”
        heredó una fracción de su genoma de ancestros de la población
        “k”.

<p align="center">

<img width="600" src="imagenes/Structure/10.jpg">

</p>

  - *Modelos de frecuencias alélicas*

    1.  **No correlacionadas:** Asume que las frecuencias alélicas en
        las poblaciones son independientes.

    2.  **Correlacionadas:** Supone que las frecuencias alélicas de
        distintas poblaciones serán muy similares (puede ser por
        migración o por ancestría compartida).

<p align="center">

<img width="600" src="imagenes/Structure/11.jpg">

</p>

  - *Uso de información a priori*

    1.  **LOCPRIOR models**: Usar los sitios de muestreo como
        información a priori para ayudar en el proceso de agrupamiento.
        Esta opción se puede considerar cuando la estructura es muy
        débil.

    2.  **USEPOPINFO model**: utiliza los sitios de muestreo para buscar
        migrantes o híbridos. También se puede usar para determinar a
        priori la ancestría de algunos individuos y ayudar en el proceso
        de agrupamiento.

<p align="center">

<img width="600" src="imagenes/Structure/12.jpg">

</p>

3.  Programar el número de repeticiones.

<p align="center">

<img width="600" src="imagenes/Structure/13.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/14.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Structure/15.jpg">

</p>

La típica forma gráfica de representar los resultados es una gráfica de
barras. De lo general a lo particular, el número de colores en la
gráfica corresponde al número de grupos genéticos (K) que nosotros
indicamos. La gráfica está dividida por líneas negras que representan
los sitios de muestreo. Por último, cada línea de color representa a un
individuo, el o los colores que tiene asignados muestran la proporción
de su genoma que proviene de cada grupo genético.

<p align="center">

<img width="600" src="imagenes/Structure/16.jpg">

</p>

En el resúmen de todas las corridas que hicimos podemos ver la
comparación de la probabilidad del genotipo dado el grupo genético. De
manera informal se sugiere que el valor más chico es el que corresponde
a la mejor elección de K. Sin embargo, esta es una desición que se debe
hacer con cuidado y teniendo en cuenta el contexto biológico de lo que
se esté analizando.

<p align="center">

<img width="600" src="imagenes/Structure/17.jpg">

</p>

Más información de cómo se usa Structure [Manual](pdf/Structure_man.pdf)

Artículo de descripción del método [Pritchard et al.,
2000](pdf/structure_prichart.pdf)

## STRUCTURE HARVESTER

Un método más formal para seleccionar la k adecuada es el de Evanno y se
puede calcular a través de la herramienta de
(<http://taylor0.biology.ucla.edu/structureHarvester/>)

El primer paso es el de comprimir la carpeta de resultados de Structure
(.zip).

<p align="center">

<img width="600" src="imagenes/Structure_Harvester/01.jpg">

</p>

Posteriormente se carga en la página que calculará los resultados.

<p align="center">

<img width="600" src="imagenes/Structure_Harvester/02.jpg">

</p>

La idea de este método es que con el estadístico arrojado por structure
Ln P(D) no es fácil reconocer qué K es la óptima. A través de una serie
de derivadas se puede tener un mejor criterio de elección.

<p align="center">

<img width="600" src="imagenes/Structure_Harvester/evanno.jpg">

</p>

[Evanno et al., 2005](pdf/Evanno.pdf) Artículo en el que se propone el
método.

## SPAGeDi

El programa Spagedi lo vamos a utilizar para inferir si hay estructura
filogeográfica, es decir, si hay una distribución no uniforme de los
alelos en el espacio en la que además los alelos más similares se
encuentren geográficamente juntos. Esto se hace comparando dos índices
de diferenciación (Nst y Gst).

![N\_{ST}](https://latex.codecogs.com/png.latex?N_%7BST%7D "N_{ST}")

Se obtiene a partir de buscar la diferencia entre la diversidad total y
la que está dentro de cada población, dividida por la diversidad total.


![\\frac{v\_{T}-v\_{S}}{v\_{T}}](https://latex.codecogs.com/png.latex?%5Cfrac%7Bv_%7BT%7D-v_%7BS%7D%7D%7Bv_%7BT%7D%7D
"\\frac{v_{T}-v_{S}}{v_{T}}")


![N\_{ST}=\\frac{\\sum\_{i,j}\\pi\_{ij}C\_{ij}}{v\_{T}}](https://latex.codecogs.com/png.latex?N_%7BST%7D%3D%5Cfrac%7B%5Csum_%7Bi%2Cj%7D%5Cpi_%7Bij%7DC_%7Bij%7D%7D%7Bv_%7BT%7D%7D
"N_{ST}=\\frac{\\sum_{i,j}\\pi_{ij}C_{ij}}{v_{T}}")

La diferencia entre
![G\_{ST}](https://latex.codecogs.com/png.latex?G_%7BST%7D "G_{ST}") y
![N\_{ST}](https://latex.codecogs.com/png.latex?N_%7BST%7D "N_{ST}") es
que ![N\_{ST}](https://latex.codecogs.com/png.latex?N_%7BST%7D "N_{ST}")
toma en cuenta las diferencias entre los haplotipos
(![\\pi](https://latex.codecogs.com/png.latex?%5Cpi "\\pi")), mientras
que ![G\_{ST}](https://latex.codecogs.com/png.latex?G_%7BST%7D "G_{ST}")
solo toma en cuenta las frecuencias.

<p align="center">

<img width="300" src="imagenes/Spagedi/pons_petit.jpg">

</p>

```
## 226  22  0   1   2   1
## 0
## ind  cat hap
## qhu001   viro    1
## qhu002   viro    1
```

    ## qhu224   chac    19
    ## qhu225   chac    20
    ## qhu226   chac    21
    ## END
    ## hap  1   2   3   4   5   6   7   8   9   10  11  12  13  14  15  16  17  18  19  20  21
    ## 1    0   1   5   2   3   2   2   5   1   2   1   2   1   3   2   4   2   5   2   3   3

El archivo de entrada se compone de:

  - un encabezado en el que se especifica el número de individuos, el
    número de poblaciones, número de coordenadas espaciales (columnas),
    numero de loci, número de dígitos por locus y ploidía.

  - un número de intervalos de distancia

  - encabezados de columnas (individuo, categoría, haplotipo)

  - una lista con todos los individuos en la primera columna, el sitio
    de muestreo al que pertenecen y el haplotipo que tiene cada uno. El
    final de la lista se especifica con “END”

  - una matriz de distancias entre haplotipos.

<p align="center">

<img width="600" src="imagenes/Spagedi/01.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/02.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/03.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/04.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/05.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/06.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/07.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/08.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/09.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/10.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/11.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Spagedi/12.jpg">

</p>

## Network

Por último vamos a crear una red de haplotipos que va a calcular las
relaciones entre los mismos. El archivo de entrada en este programa se
puede hacer de manual o en formato .rdf

<p align="center">

<img width="600" src="imagenes/Network/01.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/02.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/04.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/05.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/06.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/07.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/08.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/09.jpg">

</p>

<p align="center">

<img width="600" src="imagenes/Network/10.jpg">

</p>
