---
{"dg-publish":true,"permalink":"/linux/apps/zen-browser/"}
---


## actualizar zen browser

 - Primero se identificó dónde estaba instalado el navegador y qué versiones teníamos:
``` bash
# 1. Localizar la ruta del binario y el lanzador
which zen
ls -ld /opt/zen
cat /usr/share/applications/zen.desktop

# 2. Verificar la versión actual instalada
cat /opt/zen/application.ini | grep -E "Version|BuildID"

# 3. Inspeccionar el archivo comprimido sin descomprimir todo
tar -xvf zen.linux-x86_64.tar.xz zen/application.ini -O | grep -E "Version|BuildID"

# 4. Confirmar dónde residen los perfiles de usuario
ls -la ~/.config/zen/
```

- Para asegurarnos de que el archivo .tar.xz no estaba corrupto y que el binario funcionaba correctamente en tu  sistema (OPCIONAL):
```bash
# Crear carpeta temporal y extraer el contenido
mkdir -p /tmp/zen_test_extract
tar -xf zen.linux-x86_64.tar.xz -C /tmp/zen_test_extract

# Probar la ejecución del binario
/tmp/zen_test_extract/zen/zen --version

# Limpiar la prueba
rm -rf /tmp/zen_test_extract
```


- Para actualizar los binarios sin generar conflictos de propietarios ni romper enlaces:
```bash
mkdir -p /tmp/zen_new
tar -xf ~/Downloads/zen.linux-x86_64.tar.xz --strip-components=1 -C /tmp/zen_new

# 2. Copiar y sobrescribir los archivos del navegador en /opt/zen
cp -rf /tmp/zen_new/* /opt/zen/

# 3. Eliminar la carpeta temporal
rm -rf /tmp/zen_new
```

- Para garantizar que cualquier usuario del sistema pueda leer y ejecutar el nuevo navegador sin problemas de permisos:
```bash
chmod -R a+rX /opt/zen
```

- Confirmar que el sistema reconoce la nueva versión en todas las rutas:

```bash
# Comprobar la versión instalada en /opt y en /usr/local/bin
/opt/zen/zen --version
/usr/local/bin/zen --version

# Verificar que los perfiles sigan intactos
ls -la ~/.config/zen/
```

## Actualizaciones automatica:
```bash
mkdir -p /tmp/zen_update && \
tar -xf ~/Downloads/zen.linux-x86_64.tar.xz --strip-components=1 -C /tmp/zen_update && \
cp -rf /tmp/zen_update/* /opt/zen/ && \
chmod -R a+rX /opt/zen && \
rm -rf /tmp/zen_update && \
zen --version  
```

