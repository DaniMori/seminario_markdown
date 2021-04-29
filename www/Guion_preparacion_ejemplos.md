# Preparación

1. Abrir presentación HTML en Firefox [^warn_browser]

[^warn_browser]: Algunos elementos embebidos
(i.e. entrevista de muestreo de experiencias) no funcionan en Chrome, MS Edge,
o MS Explorer, pero sí en Firefox.

1. Abrir colección _Ejemplo_rmarkdown_ en Zotero

1. Abrir en Rstudio `www\ejemplo_Rmarkdown\Recoding_occupation.Rmd`

1. Abrir en Rstudio `www\ejemplo_Rmarkdown\Ejemplomarkdown.bib`

1. Abrir en Rstudio
   `www\ejemplo_Rmarkdown\Elsevier_submission\Elsevier_submission.Rmd`

1. Abrir en Rstudio
   `www\ejemplo_Rmarkdown\Sage_submission\Sage_submission.Rmd`

1. Abrir en Rstudio `www\ejemplo_con_Stata\sorpresa_agradable.Rmd`

1. Abrir en Rstudio `www\ejemplo_workflow\generacion_variables.Rmd`

1. Ir a carpeta `www\ejemplo_Rmarkdown` en el visor de archivos de Rstudio

1. Abrir el [Manual de sincronización de OneDrive](https://dauam-my.sharepoint.com/:b:/r/personal/marta_miret_uam_es/Documents/Edad%20con%20Salud/Documentacion%20Edad%20con%20Salud/Documentaci%C3%B3n%20transversal/Migracio%CC%81n%20a%20OneDrive/Manual_sincronizacio%CC%81n_OneDrive.pdf?csf=1&web=1&e=82zxMi)
   en el navegador
   

# Guión ejemplo

1. Exportar `.bib` desde Zotero
   (Click derecho en coleccion -> "Exportar colección..." -> OK,
   Seleccionar archivo `www/ejemplo_Rmarkdown/Ejemplomarkdown.bib`)

1. Knitear a HTML

1. Mostrar citas y referencias (CSL en formato APA, enlaces funcionales)

1. Generar bibliografía de ejemplo (mostrar `.bib` en encabezado yaml)

1. Añadir referenica faltante ([@kahneman_developments_2006])

1. Knitear a Word

1. Añadir `reference_docx: APA_6th_like_simple.dotx` a salida `word_document`,
   cambiar `.csl` a `apa-old-doi-prefix.csl`,
   y knitear de nuevo a Word

1. Knitear a PDF

1. Ejemplo Elsevier
   (knitear `www/ejemplo_Rmarkdown/Elsevier_submission/Elsevier_submission.Rmd`
   y mostrar salida en LaTeX)

1. Ejemplo Springer
   (copiar todo menos el encabezado del ejemplo Elsevier,
   knitear `www/ejemplo_Rmarkdown/Sage_submission/Sage_submission.Rmd`
   y mostrar salida en LaTeX)

1. Ejemplo con Stata (knitear `www/ejemplo_con_Stata/sorpresa_agradable.Rmd`)

1. Ejemplo Workflow (knitear `www/ejemplo_workflow/generacion_variables.Rmd`)
