# Introducción

Proyecto de presentación para seminario sobre Markdown en la
Universidad Autónoma de Madrid, junio de 2020.

Este seminario se realizará online en el grupo del
Centro Colaborador de la Organización Mundial de la Salud
(Departamento de Psiquiatría, Facultad de Medicina)


Para knitear y ejecutar la presentación en un navegador, es necesario:

1. Disponer de R y Rstudio

1. Instalar el paquete `revealjs` (`install.packages("revealjs")`)

1. Para _knitear_ los documentos
   `www\ejemplo_Rmarkdown\Recoding_occupation.Rmd` y
   `www\ejemplo_con_Stata\sorpresa_agradable.Rmd` es necesario generar
   el dataset a partir del archivo maestro de línea base
   de Edad con Salud (ver abajo)
   
1. Para _knitear_ el documento
   `www\ejemplo_Rmarkdown\Elsevier_submission\Elsevier_submission.Rmd`
   es necesario además el paquete `rticles` (`install.packages("rticles")`)

1. Para _knitear_ el documento
   `www\ejemplo_Rmarkdown\Sage_submission\Elsevier_submission.Rmd`
   es necesario además el paquete `rticles`, y además, copiar en el documento
   el contenido del cuerpo del documento anterior
   (todo menos el encabezado YAML)

1. Otros paquetes de R aparecen en el chunk `setup` de cada documento,
   justo a continuación del encabezado YAML


# Atribuciones

- Las atribuciones de todas las imágenes utilizadas se encuentran en la presentación

- Los siguientes archivos:

```
www\ejemplo_Rmarkdown\Elsevier_submission\elsevier-harvard.csl
www\ejemplo_Rmarkdown\Sage_submission\sagej.cls
www\ejemplo_Rmarkdown\Sage_submission\sageh.bst
```
  
  se distribuyen con el paquete `rticles` y sus licencias se encuentran en él.



# Generar dataset para Stata

```r
library(haven)
library(magrittr)
library(dplyr)
library(stringr)

bl_data <- read_sav("<BASE_DIR>/Universidad Autonoma de Madrid/marta.miret@uam.es - Bases de datos maestras Edad con Salud/Ola_1_Linea_base/All_COURAGE_VFINAL.sav")

bl_data %>%
  mutate(Q1510_CATOCCFINAL = Q1510_CATOCCFINAL %>% str_remove("[^0-9]+")) %>%
  write_dta("dat/ecs_base.dta")
```
