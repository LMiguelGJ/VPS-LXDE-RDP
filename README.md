# README — How to Get Free Windows RDP

Este README explica los pasos y comandos para preparar un RDP "gratuito" en una instancia Linux, y cómo exponerlo vía túnel con **pinggy.io**.


## Requisitos

* Acceso root a la instancia (SSH).
* `curl`, `apt` disponibles.

---

## Comandos paso a paso

Ejecuta los siguientes comandos en la instancia (uno por uno):

1. Actualizar paquetes

```bash
apt update
```

2. Instalar `neofetch` (opcional, muestra info del sistema)

```bash
apt install neofetch
```

3. Ejecutar `neofetch` para ver información del sistema

```bash
neofetch
```

4. Descargar y ejecutar el script principal (vpsfree)

```bash
curl -s https://raw.githubusercontent.com/abdalla435/VPS-Pterodactyl-EGG/main/vpsfree.sh -o main.sh && bash main.sh
```

5. Instalar `sudo` (si fue removido previamente por el script)

```bash
apt install sudo
```

6. Establecer contraseña de `root` (o del usuario que vayas a usar)

```bash
sudo passwd
```

---

## Datos RDP por defecto (según el script)

* **RDP Port:** `3389`
* **Username:** `root`
* **Password:** `root`

---

## Conectar por RDP a través de un túnel (pinggy.io)

El script indica que para acceder por RDP debes crear un túnel usando **pinggy.io** y seleccionar `TCP` con el mismo puerto (HTTP / HTTPS Tunnel).

### Comando para iniciar el túnel

Ejecuta este comando localmente (o en la instancia) para crear el túnel SSH:

```bash
ssh -p 443 -R0:127.0.0.1:3389 -L4300:127.0.0.1:4300 -o StrictHostKeyChecking=no -o ServerAliveInterval=30 b2b6xseqZNZ@free.pinggy.io
```

* Esto crea un reenvío remoto del puerto RDP (`3389`) a través del servicio de pinggy.
* También abre un túnel local en el puerto `4300` para acceder al *Web Debugger*.

### Web Debugger / URL local

* **Web Debugger URL:** `http://localhost:4300/`
* **Local address (RDP):** `http://localhost:3389`

> Puedes configurar un subdominio persistente desde las opciones de `custom subdomain` en pinggy para obtener una URL estable.

---

## Plataforma

* **Client:** Windows (usar Remote Desktop Connection o cliente RDP compatible).

## Access token / Credenciales de Pinggy (tal como proporcionadas)

* **Access token:** `b2b6xseqZNZ`
* **Region:** (si aplica) — verificar en la consola de pinggy.



