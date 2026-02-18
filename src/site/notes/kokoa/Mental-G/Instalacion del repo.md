---
{"dg-publish":true,"permalink":"/kokoa/mental-g/instalacion-del-repo/"}
---

en el repo estan los pasas pero algo incompleto
debes abres la terminal y ejecutas estos comandos

1. Clonar el repositorio
	- `git clone cd kokoa-analisis-salud-mental` 
2. Crear el entorno virtual
	-`python -m venv venv` o `python3 -m venv venv` o`py -m venv venv` el que te sirva para tu OS
3. Activar el entorno virtual
	- `venv\Scripts\activate`
4. Instalar dependencias
	- `pip install -r requirements.txt` 
	- si hay un error deberias modificar el archivo **requirements.txt** asi:
		- vas a la carpeta y abres este archivo![Pasted image 20260218144712.png](/img/user/imagen/Pasted%20image%2020260218144712.png)
		- y le quitas los iguales, debe quedar asi:
		![Pasted image 20260218144808.png](/img/user/imagen/Pasted%20image%2020260218144808.png)	
		- lo guardas y ejecutas de nuevo el `pip install -r requirements.txt`
		- Nota: por lo visto, en el proyecto hay documentos que usan librerias que no estan en `requirements.txt` y no se podra ejecutar ese codigo, se lo mencionara cuando sea pertienente

## configurar el espacio de trabajo
1. Instalar y abrir visual studio code
2. instalar las siguientes extensiones:
	- CSV, Jupyter, Python ![Pasted image 20260218145617.png](/img/user/imagen/Pasted%20image%2020260218145617.png)
## Probar notebook

Ya puedes ejecutar el codigo, pero si no te corre o da error, lo mas probable es que visual code no reconoce el entorno virtual y lo tienes que configurar por tu cuenta te recomiendo hacer lo siguiente:

lo mas seguro es montar el entorno virtual en la vscode asi:
![[Screencast From 2026-02-18 15-12-42.mp4]]

y ya lo puedes ejecutar