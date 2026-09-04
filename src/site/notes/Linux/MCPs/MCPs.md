---
{"dg-publish":true,"permalink":"/linux/mc-ps/mc-ps/"}
---

# Gemini Spark
Para conectarme a un mcp remoto debes buscar uno muy famoso y que tenga un MCP remoto como github o algo asi, pero para los que no puedes usar webs pero te permiten probarlas como por ejemplo
- Glama
Y esta ultima menciona una forma para usar tu maquina para exponer tu mcp y los de glama hacen de proxy asi
## Expose Local MCP Servers

Test your local MCP servers with the inspector by exposing them via a public tunnel using [mcp-proxy](https://github.com/punkpeye/mcp-proxy).

```
# Expose your MCP server via a public tunnel
npx mcp-proxy --port 8080 --tunnel -- tsx server.js

# Request a specific subdomain
npx mcp-proxy --port 8080 --tunnel --tunnelSubdomain myapp -- tsx server.js

# When the tunnel is established, you'll see a message like:
tunnel established at https://bright-wombat-83.tunnel.gla.ma
```

Once the tunnel is established, you can use the provided URL to connect to your local server in the inspector.

## Mis mcp con proxy de glama
yo uso el mcp de canvas lms y uso este script para conectarme
``` bash
CANVAS_API_TOKEN="TU_TOKEN_DE_CANVAS" \
CANVAS_BASE_URL="https://tu-institucion.instructure.com" \
npx mcp-proxy --port 8080 --tunnel -- npx -y @r-huijts/canvas-mcp
```

se ve asi:
![Pasted image 20260807213531.png](/img/user/imagen/Pasted%20image%2020260807213531.png)

## Con docker 
Para hacer mejor lo puedo hacer en docker y lo hago asi:
### primero realizo un archivo doker file
``` dockerfile
FROM node:20-slim

WORKDIR /app

# Instalar npx y dependencias necesarias
RUN npm install -g mcp-proxy @r-huijts/canvas-mcp

# Exponer el puerto del proxy
EXPOSE 8080

# Comando para ejecutar el proxy con el túnel
CMD ["npx", "mcp-proxy", "--port", "8080", "--tunnel", "--tunnelSubdomain", "mi-canvas-mcp", "--", "npx", "@r-huijts/canvas-mcp"]
```
Despues ejecutamos la imagen
``` bash
docker build -t canvas-mcp-proxy .
```
### despues la ejecucion
``` bash
docker run -d \
  --name canvas-mcp \
  --restart unless-stopped \
  -e CANVAS_API_TOKEN="TU_TOKEN_DE_CANVAS" \
  -e CANVAS_BASE_URL="https://tu-institucion.instructure.com" \
  canvas-mcp-proxy
```

Se veria algo asi:
![Pasted image 20260807214432.png](/img/user/imagen/Pasted%20image%2020260807214432.png)

Y despues cojemos el url con los logs:
``` bash
docker logs canvas-mcp
```

## Conectarlo al spark
Solo pegar el link en conectores mcp y no olvidar poner mcp en la parte final
![Pasted image 20260807214621.png|581](/img/user/imagen/Pasted%20image%2020260807214621.png)

Y apareceria algo asi:
![Pasted image 20260807214644.png|474](/img/user/imagen/Pasted%20image%2020260807214644.png)
![Pasted image 20260807214652.png|188](/img/user/imagen/Pasted%20image%2020260807214652.png)
