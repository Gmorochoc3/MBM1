# INFORME DEL PROYECTO FINAL DE HERRAMIENTAS ÓMICAS I
## INTEGRANTES  
## TEMA  
## PROBLEMA BIOLÓGICO
La resistencia antimicrobiana (RAM) es considerada una de las principales amenazas para la salud pública mundial debido al aumento de bacterias multirresistentes que disminuyen la eficacia de los tratamientos antibióticos. *Pseudomonas aeruginosa* es un patógeno oportunista asociado principalmente a infecciones hospitalarias y posee una elevada capacidad para desarrollar resistencia mediante bombas de eflujo, mutaciones cromosómicas y adquisición de genes de resistencia a través de plásmidos y otros elementos móviles (Pang et al., 2019). Además, esta bacteria ha sido catalogada por la Organización Mundial de la Salud (OMS) como un patógeno prioritario crítico para el desarrollo de nuevos antibióticos (WHO, 2024).

En este proyecto se busca identificar genes de resistencia antimicrobiana presentes en dos diferentes aislados clínicos de *Pseudomonas aeruginosa* mediante el uso de herramientas ómicas y análisis bioinformático.  

## PREGUNTA DE INVESTIGACIÓN
¿Qué genes de resistencia antimicrobiana pueden identificarse mediante el ensamblaje y análisis bioinformático de diferentes aislados clínicos de *Pseudomonas aeruginosa*?   

## OBJETIVOS
Objetivo general
Identificar genes de resistencia antimicrobiana y secuencias plasmídicas presentes en diferentes aislados clínicos de Pseudomonas aeruginosa mediante ensamblaje de novo y análisis bioinformático.

Objetivos específicos
• Realizar el control de calidad de las lectura s genómicas obtenidas de diferentes aislados clínicos de Pseudomonas aeruginosa.
• Ensamblar los genomas bacterianos utilizando herramientas de ensamblaje de novo.
• Detectar genes de resistencia antimicrobiana utilizando bases de datos específicas.
• Comparar los perfiles de resistencia antimicrobiana entre los diferentes aislados clínicos analizados.


## INTRODUCCIÓN  
## DESARROLLO Y RESULTADOS    
### Obtención y preparación de datos 
Se realizó una búsqueda en la base de datos pública Sequence Read Archive (SRA) del National Center for Biotechnology Information (NCBI), donde se utilizó la terminología “*Pseudomonas aeruginosa* clinical isolate nanopore”, como se muestra en la Figura X.   

Figura x. Búsqueda de “Pseudomonas aeruginosa clinical isolate nanopore” en NCBI.  
<img width="1480" height="900" alt="c" src="https://github.com/user-attachments/assets/05b71173-db52-434a-9b0f-a370fc3516fe" />  

La selección de las secuencias de trabajo se realizó considerando que los aislados clínicos fueran de diferente procedencia, de lo cual resultaron dos genomas de *Pseudomonas aeruginosa*, identificadas como: WGS of Pseudomonas aeruginosa: isolate PS2045 long reads (SRR37232887) (Figura x) y  Nanopore MinION sequencing reads of Pseudomonas aeruginosa ST175 clinical isolate ST175LTH (SRR32362393) (Figura x).

Figura X. Detalle de la búsqueda de la secuencia SRR37232887 del genoma de *P. aeruginosa* en la base de datos NCBI.  
<img width="1664" height="882" alt="b" src="https://github.com/user-attachments/assets/b3af391a-2cb4-49fa-ba76-bbe828e7a8f2" />  

Figura X. Detalle de la búsqueda de la secuencia SRR32362393 del genoma de *P. aeruginosa* en la base de datos NCBI.   
<img width="1908" height="881" alt="a" src="https://github.com/user-attachments/assets/0b19a38d-c032-4f03-bb5d-fdeba807e219" />  

Los datos genómicos descasrgados en formato FASTQ fueron almacenados en zenodo: 
### Control de calidad de datos    
### Ensamblaje de novo     
### Identificación de plásmidos  
### Análisis de resistencia antimicrobiana  

## CONCLUSIONES   
## BIBLIOGRAFÍA
Pang, Z., Raudonis, R., Glick, B. R., Lin, T. J., & Cheng, Z. (2019). Antibiotic resistance in *Pseudomonas aeruginosa*: Mechanisms and alternative therapeutic strategies. Biotechnology Advances, 37(1), 177–192. https://doi.org/10.1016/j.biotechadv.2018.11.013 
World Health Organization. (2024). Antimicrobial resistance. WHO – Antimicrobial resistance
