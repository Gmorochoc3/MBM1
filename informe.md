# INFORME DEL PROYECTO FINAL DE HERRAMIENTAS ÓMICAS I
## INTEGRANTES 
José Proaño  
Génesis Morocho  
Mayra Erazo  
Samanta Bucheli  
Michelle Yugcha  
## TEMA 
Identificación de genes de resistencia antimicriobiana de aislados clínicos de *Pseudomonas aeruginosa*

## INTRODUCCIÓN
La resistencia antimicrobiana (RAM) es considerada una de las principales amenazas para la salud pública mundial debido al aumento de bacterias multirresistentes que disminuyen la eficacia de los tratamientos antibióticos. *Pseudomonas aeruginosa* es un patógeno oportunista asociado principalmente a infecciones hospitalarias y posee una elevada capacidad para desarrollar resistencia mediante bombas de eflujo, mutaciones cromosómicas y adquisición de genes de resistencia a través de plásmidos y otros elementos móviles (Pang et al., 2019). Además, esta bacteria ha sido catalogada por la Organización Mundial de la Salud como un patógeno prioritario crítico para el desarrollo de nuevos antibióticos (WHO, 2024).  

En este proyecto se busca identificar genes de resistencia antimicrobiana presentes en aislados clínicos de *Pseudomonas aeruginosa* mediante el uso de herramientas ómicas. 

## PREGUNTA DE INVESTIGACIÓN
¿Qué genes de resistencia antimicrobiana pueden identificarse mediante el ensamblaje y análisis bioinformático de diferentes aislados clínicos de *Pseudomonas aeruginosa*?   

## OBJETIVOS
Objetivo general:  
Identificar genes de resistencia antimicrobiana y secuencias plasmídicas presentes en diferentes aislados clínicos de *Pseudomonas aeruginosa* mediante ensamblaje de novo y análisis bioinformático.

Objetivos específicos:  
• Realizar el control de calidad de las lectura s genómicas obtenidas de diferentes aislados clínicos de *Pseudomonas aeruginosa*.  
• Ensamblar los genomas bacterianos utilizando herramientas de ensamblaje de novo.    
• Detectar genes de resistencia antimicrobiana utilizando bases de datos específicas.  
• Comparar los perfiles de resistencia antimicrobiana entre los diferentes aislados clínicos analizados.  

## DESARROLLO Y RESULTADOS

## Herramientas empleadas
SRA: descarga de secuencias crudas a partir de CNBI.

FastQC: revisión de calidad de lecturas

Trim Galore: permite la limpieza de los datos crudos

SPAdes: formación de conting

PlastFlow: predicción de ADN plasmídico o cromosómico

Staramr: buscar genes de resistencia

WORKFLOW

### Obtención y preparación de datos 

Se realizó una búsqueda en la base de datos pública Sequence Read Archive (SRA) del National Center for Biotechnology Information (NCBI), donde se utilizó la terminología “*Pseudomonas aeruginosa* clinical isolate illumina”, como se muestra en la Figura 1.   

Figura 1. Búsqueda de “Pseudomonas aeruginosa clinical isolate nanopore” en NCBI. 

<img width="1480" height="900" alt="c" src="https://github.com/user-attachments/assets/05b71173-db52-434a-9b0f-a370fc3516fe" />  

La selección de las secuencias de trabajo se realizó considerando que los aislados clínicos fueran de diferente procedencia, de lo cual resultaron dos genomas de *Pseudomonas aeruginosa*, identificadas como: SRR38509012; SRR38520180, como se muestra en las Figura 2 y Figura3.

Figura 2. Detalle de la búsqueda de la secuencia SRR38509012  
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/dfa00931-27b7-4201-ad05-4fd02f57b42d" />


Figura 3. Detalle de la búsqueda de la secuencia SRR38520180  
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/3a077da7-632d-416c-ab16-83e4f62d2287" />  


El proceso de descarga se lo realizo utilizando el comando prefetch como se lo vizualiza en la Figura 4
Se utilizo este comando ya que nos ayuda a tener una descarga mas eficiente y mas rapida en relacion a la que nos da NCBI

Figura 4. Utilización del comando prefetch

<img width="492" height="313" alt="image" src="https://github.com/user-attachments/assets/a43fc38d-fa80-42a9-afdd-bac47a507cea" /> 

Posterior a ello se lo convirtio en formato fastq con el comando fasterq-dump SRR38520180 --split-files

Figura 5. Utilización de comando fasterq-dump    

<img width="824" height="318" alt="image" src="https://github.com/user-attachments/assets/86d03c3b-b29b-4f0e-9bb5-234246ac44a7" />  


<img width="498" height="110" alt="image" src="https://github.com/user-attachments/assets/2e09b630-d602-4e1a-bb38-5b2921649d89" />


### Control de calidad de datos  
Para el control de calidad se utilizo el comando fastqc *.fastq -t 8 con el cual nos ayuda a correr todos los archivos en conjunto  
Figura 6. Aplicación de comando fastqc -t 8

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/e0d7b9b2-5324-44a5-a434-5cdbcca7ff0e" />

### Limpieza de lecturas
Para la limpieza y eliminacion de adaptadores se utilizo tringalore con el codigo trim_galore --paired --phred33 --cores 4 --quality 30 --length 30 --gzip --output_dir TrimmedReads -a 
"file:./my_adapters.fa" -a2 "file:./my_adapters.fa" /home/usuario/Escritorio/PF/SRR38520180_1.fastq /home/usuario/Escritorio/PF/SRR38520180_2.fastq  

Figura 7. Uso de la herramienta trimgalore para limpieza de lecturas  
<img width="924" height="376" alt="image" src="https://github.com/user-attachments/assets/462bd062-283f-46dd-979d-61794e194840" />  


Figura 8. Uso de la herramienta trimgalore para limpieza de lecturas

<img width="343" height="388" alt="image" src="https://github.com/user-attachments/assets/81ea1002-1009-4c14-bb94-c44209e7d91f" />


### Ensamblaje de novo   
Para el ensable de los datos obtenidos se utilizo Spades: spades.py -1 TrimmedReads/SRR38509012_1_val_1.fq.gz -2 TrimmedReads/SRR38509012_2_val_2.fq.gz -o Output_Spades/SRR38509012 -t 8 -m 15

Figura 9. Ensamblaje de novo con herramienta spades  

<img width="931" height="746" alt="image" src="https://github.com/user-attachments/assets/6a5e6ef8-b32d-4479-b158-528fff683575" />  


<img align="left" width="352" height="350" alt="image" src="https://github.com/user-attachments/assets/55d7bbb9-bda1-4424-9d10-80fdef476317" />  



Donde vamos a tener los sguientes archivos  


Figura 10. Resultado del uso de la herramienta spades  



<img width="432" height="966" alt="image" src="https://github.com/user-attachments/assets/f32bb00c-bf76-4957-a99f-43f26fb85819" />  

### Análisis de resistencia antimicrobiana  

Los datos genómicos descargados     que contiene los contigs en formato FASTA fueron almacenados en zenodo: https://doi.org/10.5281/zenodo.20171964. 

El análisis de la resistencia antimicrobiana se realizó utilizando la plataforma Galaxy, y se hizo uso del tutorial "Antibiotic resistance detection" que se encuentra en el siguiente enlace: https://training.galaxyproject.org/training-material/topics/microbiome/tutorials/plasmid-metagenomics-nanopore/tutorial.html.   
Se creó un History denominado "Genes de resistencia en aislados de Pseudomonas aeruginosa" con el link de acceso: https://galaxy-main.usegalaxy.org/u/michelle_yugcha/h/genes-de-resistencia-en-aislados-de-pseudomonas-aeruginosa

## APLICACIONES

En un estudio realizado en Colombia se identificaron 139 pacientes con infección por Pseudomonas aeruginosa, de los cuales 54 presentaron cepas multirresistentes (resistentes a tres o más grupos de antibióticos) y 85 aislamientos sensibles a un máximo de dos grupos antimicrobianos. Estos hallazgos evidencian la elevada prevalencia de resistencia bacteriana en entornos hospitalarios y su impacto en la complejidad terapéutica.

De manera complementaria, otro estudio reportó la presencia de cepas portadoras de los genes blaKPC-2 y blaVIM-2 en pacientes hospitalizados, genes asociados a mecanismos de resistencia a carbapenémicos. Este hallazgo resalta el alto riesgo clínico que representan estas bacterias multirresistentes, debido a la limitada disponibilidad de opciones terapéuticas eficaces y al potencial incremento en la morbimortalidad hospitalaria.

## CONCLUSIONES   

Se estableció un diagrama de flujo junto con la validación otorgada por BUSCO, se estableció un metodología factible para la identificación de genes de resistencia antimicrobiana.

Se reconstruyó genomas bacterianos por medio de librerias SRR38520180 y SRR38509012 arrojando contigs.

## BIBLIOGRAFÍA
Pang, Z., Raudonis, R., Glick, B. R., Lin, T. J., & Cheng, Z. (2019). Antibiotic resistance in *Pseudomonas aeruginosa*: Mechanisms and alternative therapeutic strategies. Biotechnology Advances, 37(1), 177–192. https://doi.org/10.1016/j.biotechadv.2018.11.013   
World Health Organization. (2024). Antimicrobial resistance. WHO – Antimicrobial resistance
Pacheco T, Bustos-Cruz RH, Abril D, Arias S, Uribe L, Rincón J, García JC, Escobar-Perez J. Pseudomonas aeruginosa Coharboring BlaKPC-2 and BlaVIM-2 Carbapenemase Genes. Antibiotics (Basel). 2019 Jul 20;8(3):98. doi: 10.3390/antibiotics8030098. PMID: 31330771; PMCID: PMC6784026. https://pmc.ncbi.nlm.nih.gov/articles/PMC6784026/pdf/antibiotics-08-00098.pdf
Cuesta, D., Vallejo, M., Guerra, K., Cárdenas, J., Hoyos, C., Loaiza, E., & Villegas, M. V. (2012). Infección intrahospitalaria por Pseudomonas aeruginosa multirresistente: Estudio de casos y controles. Medicina U.P.B., 31(2), 135–142. file:///C:/Users/Samanta/Downloads/ezapatarestrepo,+Art%C3%ADculo+original+5.pdf
