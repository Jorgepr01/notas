---
{"dg-publish":true,"permalink":"/linux/apps/configuracion-de-dunst-y-monitor-de-bateria/"}
---

Documentación del entorno de notificaciones para **i3wm**, **Polybar** y **Picom**.

---

# 1. Archivos del Sistema

* **Configuración de Dunst:** [`dunstrc`](file:///home/jorge_dev/.config/dunst/dunstrc)
* **Script del Monitor:** [`scripts/battery-monitor.sh`](file:///home/jorge_dev/.config/dunst/scripts/battery-monitor.sh)
* **Servicio Systemd:** [`~/.config/systemd/user/battery-monitor.service`](file:///home/jorge_dev/.config/systemd/user/battery-monitor.service)

---

# 2. Personalización Visual (Gruber Darker)


* **Fondo:** `#282828` (gris oscuro suave).
* **Tipografía:** `JetBrains Mono 10`.
* **Grosor del marco:** `2px` (`frame_width = 2`, `separator_height = 2`).
* **Bordes redondeados:** `corner_radius = 8`.
* **Margen vertical:** Ajustado a `(16, 46)` para posicionarse debajo de la barra Polybar.
* **Colores por urgencia:**
  * **Baja:** Borde azul pizarra (`#96A6C8`).
  * **Normal:** Borde amarillo (`#FFDD33`).
  * **Crítica:** Borde rojo (`#F43841`).

---

# 3. Alertas de Batería

El monitor consulta el kernel (`/sys/class/power_supply/`) cada 30 segundos y gestiona:
* **Eventos de cable:** Alerta al conectar o desconectar el cargador.
* **Carga completa:** Alerta al llegar al 100%.
* **Umbrales de descarga:**
  * `<= 20%`: Advertencia normal.
  * `<= 10%`: Advertencia crítica.
  * `<= 5%`: Alerta de emergencia.
* **Anti-spam:** Emplea identificadores de reemplazo (`-r 9991` y `-r 9992`) para evitar notificaciones repetidas acumuladas.

---

# 4. Comandos de Gestión

```bash
# Estado del servicio de batería
systemctl --user status battery-monitor.service

# Ver logs del monitor en tiempo real
journalctl --user -u battery-monitor.service -f

# Reiniciar monitor de batería
systemctl --user restart battery-monitor.service

# Reiniciar Dunst (tras modificar dunstrc)
systemctl --user restart dunst
```
