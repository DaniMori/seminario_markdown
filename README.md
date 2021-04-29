# Introducción

Proyecto de presentación para seminario sobre Markdown en la
Universidad Autónoma de Madrid.

Este seminario se ha realizado online dos veces:

- Para el grupo del Centro Colaborador de la Organización Mundial de la Salud
(CCOMS, Departamento de Psiquiatría, Facultad de Medicina),
el 25 de junio de 2020.

- Para el equipo del proyecto Edad con Salud
(con miembros del CCOMS y del Parc Sanitari San Joan de Deu de Barcelona),
el 29 de abril de 2021.


Para knitear y ejecutar la presentación en un navegador, es necesario:

1. Disponer de R y Rstudio

1. Instalar el paquete [`revealjs`](https://cran.r-project.org/package=revealjs)
(`install.packages("revealjs")`)

1. Para _knitear_ los documentos
   `www\ejemplo_Rmarkdown\Recoding_occupation.Rmd` y
   `www\ejemplo_con_Stata\sorpresa_agradable.Rmd` es necesario generar
   el dataset a partir del archivo maestro de línea base
   de Edad con Salud (ver abajo)
   
1. Para _knitear_ el documento
   `www\ejemplo_Rmarkdown\Elsevier_submission\Elsevier_submission.Rmd`
   es necesario además el paquete
   [`rticles`](https://cran.r-project.org/package=rticles)
   (`install.packages("rticles")`)

1. Para _knitear_ el documento
   `www\ejemplo_Rmarkdown\Sage_submission\Elsevier_submission.Rmd`
   es necesario además el paquete
   [`rticles`](https://cran.r-project.org/package=rticles),
   y además, copiar en el documento
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
  
  se distribuyen con el paquete
  [`rticles`](https://cran.r-project.org/package=rticles)
  y sus licencias se encuentran en él.



# Generar dataset para Stata

El siguiente código genera el dataset para los ejemplos con Stata
`www\ejemplo_Rmarkdown\Recoding_occupation.Rmd` y
`www\ejemplo_con_Stata\sorpresa_agradable.Rmd`.
Para poder ejecutar este código es necesario:

- Tener acceso (al menos de lectura) a la
[carpeta de Bases de Datos de Edad con Salud][1]
en el servidor OneDrive de la Universidad Autónoma de Madrid.

[1]: https://dauam-my.sharepoint.com/:f:/r/personal/marta_miret_uam_es/Documents/Edad%20con%20Salud/Bases%20de%20datos%20maestras%20Edad%20con%20Salud?csf=1&web=1&e=Hid0Ay

- Tener esta carpeta [sincronizada localmente][2]

[2]: https://support.microsoft.com/es-es/office/agregar-carpetas-compartidas-a-onedrive-y-sincronizarlas-8a63cd47-1526-4cd8-bd09-ee3f9bfc1504

- Sustituir en la línea 8 los caracteres `<BASE_DIR>`
(con los símbolos `<>` incluidos, pero dejando las comillas `"`)
por la ruta en la que se encuentre la carpeta raíz de las carpetas compartidas
de OneDrive de la UAM.
En Windows, normalmente se habrá creado en la carpeta de configuración de
usuario, así que bastaría con sustituir `<BASE_DIR>` por `~/..`.

**NOTA:** Si la instalación de OneDrive y la sincronización de las carpetas es
antigua, es posible que la carpeta raíz de las carpetas compartidas de OneDrive
se llame `Universidad Autonoma de Madrid` en lugar de `UAM`.
Esto se debe a que la UAM utilizó anteriormente este identificador y después
lo cambió para evitar problemas con las rutas de archivo largas.
Si es el caso, modificar la ruta de archivo correspondientemente en la línea 9.

```r
library(haven)
library(magrittr)
library(dplyr)
library(stringr)

bl_data <- read_sav(
  file.path(
    "<BASE_DIR>",
    "UAM",
    "marta.miret@uam.es - Bases de datos maestras Edad con Salud",
    "Ola_1_Linea_base",
    "All_COURAGE_VFINAL.sav"
  )
)

bl_data %>%
  mutate(Q1510_CATOCCFINAL = Q1510_CATOCCFINAL %>% str_remove("[^0-9]+")) %>%
  write_dta("dat/ecs_base.dta")
```
