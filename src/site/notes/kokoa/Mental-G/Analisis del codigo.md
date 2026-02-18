---
{"dg-publish":true,"permalink":"/kokoa/mental-g/analisis-del-codigo/"}
---

# Carpeta de data
/data
tiene 2 subcarpetas donde 
raw/ -> tiene los csv originales donde esta la data cruda
interim/ -> tiene ya cambiados los nombres de la colummna

# Carpeta notebooks
/notebooks
Archivos:
	`00-convert-xpt-to-csv` solo los pasa a csv - no hay archivos xpt y por ende no se puede ejecutar
	`01_exploracion_datos.ipynb` solo cambia los nombre de las colummna y los pasa a otra carpeta llamada /interim
	`02_limpieza_y_preprocesamiento.ipynb` La mas intersante aqui hay mas informacion [[kokoa/Mental-G/revision de 02-limpieza\|revision de 02-limpieza]]
	`03_ingenieria_de_variables.ipynb` solo son pruebas de analisis de vision por computadora, se deben instalar las librerias que se usan
	`04_modelado_y_evaluacion.ipynb` recoordiatorio de como hacer graficos basicos en matplotlib
	`05_visualizacion_final.ipynb` usa una data que no esta en el repo de github
