# MBM_G1  
# Proyecto: Identificación de genes de resistencia antimicriobiana de diferentes aislados clínicos de Pseudomonas aeruginosa    
## Integrantes  
- José Proaño  
- Génesis Morocho  
- Mayra Erazo 
- Samanta Bucheli  
- Michelle Yugcha
## Pregunta de investigación
¿Qué genes de resistencia antimicrobiana pueden identificarse mediante el ensamblaje y análisis bioinformático de diferentes aislados clínicos de Pseudomonas aeruginosa? 
  
## Objetivos  
### Objetivo general  
Identificar genes de resistencia antimicrobiana y secuencias plasmídicas presentes en diferentes aislados clínicos de Pseudomonas aeruginosa mediante ensamblaje de novo y análisis bioinformático.
### Objetivos específicos
•  Realizar el control de calidad de las lecturas genómicas obtenidas de diferentes aislados clínicos de Pseudomonas aeruginosa.   
•  Ensamblar los genomas bacterianos utilizando herramientas de ensamblaje de novo.   
•  Detectar genes de resistencia antimicrobiana utilizando bases de datos específicas.    
•  Comparar los perfiles de resistencia antimicrobiana entre los diferentes aislados clínicos analizados.  
## Dataset  
Las secuencias fueron obtenidas desde la base de datos pública Sequence Read Archive (SRA) del National Center for Biotechnology Information (NCBI), la cual almacena datasets de secuenciación genómica generados en investigaciones científicas.  
Se utilizarán secuencias genómicas en formato FASTQ de dos diferentes aislados clínicos de Pseudomonas aeruginosa provenientes de secuenciación de lecturas largas mediante tecnología illumina, este tipo de datos permite trabajar con lecturas reales o en crudo de secuenciación genómica.   
Las secuencias de trabajo fueron las siguientes:     
1.	Pseudomonas aeruginosa: Illumina sequencing of 2026CB-00371 (SRR38520180)    
Tamaño: 151.8MB  
Contenido de GC: 65.8%   
Fecha de publicación: 026-05-12    
  
2.	Pseudomonas aeruginosa genomic sequencing of bacterial isolate 2026CH_00024 (SRR38509012)  
Tamaño: 94.5MB  
Contenido de GC: 66%  
Fecha de publicación: 2026-05-11  
  

## Flujo de trabajo  
```mermaid
flowchart TD

%% PASO 1
A[INPUT<br/>Datos SRA - NCBI<br/>SRR38520180<br/>SRR38509012]

A --> B[TOOL<br/>Descarga de secuencias<br/>prefetch]

B --> C[OUTPUT<br/>Archivos FASTQ crudos]

%% PASO 2
C --> D[TOOL<br/>Control de calidad<br/>FastQC]

D --> E[OUTPUT<br/>Reportes de calidad HTML]

%% PASO 3
E --> F[TOOL<br/>Limpieza de lecturas<br/>TrimGalore]

F --> G[OUTPUT<br/>Lecturas filtradas y limpias]

%% PASO 4
G --> H[TOOL<br/>Ensamblaje de novo<br/>SPAdes]

H --> I[OUTPUT<br/>Contigs ensamblados]

%% PASO 5
I --> J[TOOL<br/>Evaluación del ensamblaje<br/>QUAST / Bandage]

J --> K[OUTPUT<br/>Reporte del ensamblaje]

%% PASO 6
I --> L[TOOL<br/>Detección de genes AMR<br/>CARD / ResFinder / AMRFinderPlus]

L --> M[OUTPUT<br/>Genes de resistencia antimicrobiana detectados]
```
## Resultados  
## Contribución individual  
Resumen breve  
## Cómo reproducir (scripts)

## Tutorial de Galaxy
Willem de Koning, Saskia Hiltemann, Detección de resistencia a antibióticos (Materiales de capacitación de Galaxy) . https://training.galaxyproject.org/training-material/topics/microbiome/tutorials/plasmid-metagenomics-nanopore/tutorial.html En línea; consultado el miércoles 13 de mayo de 2026.
