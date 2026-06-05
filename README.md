<div align="center">

# Homelab-as-Code

### Mi laboratorio para aprender a ser Sysadmin Junior

<img width="80%" alt="Homelab banner" src="https://github.com/user-attachments/assets/1e71fbdc-1324-48e5-b2eb-f9e6c14a07c9" />

<br><br>

## ¿Qué estoy aprendiendo?

**1. VirtualBox (base para luego usar Proxmox)**<br>
Crear máquinas virtuales dentro de mi PC, como si tuviera varios ordenadores en uno. Es el primer paso antes de montar un servidor real con Proxmox.

**2. Linux Debian 13**<br>
El sistema operativo que usan la mayoría de servidores. Aprendo a instalarlo, actualizarlo y manejarlo desde terminal.

**3. SSH y terminal**<br>
Conectarme a mis máquinas sin pantalla, como se hace en empresas, usando Windows Terminal.

**4. Ansible**<br>
Escribir "playbooks" para instalar programas y configurar usuarios en todas las máquinas a la vez, sin entrar una por una.

**5. Terraform**<br>
Escribir una "receta" en código para crear máquinas virtuales automáticamente (primero en VirtualBox, luego en Proxmox).

**6. Git y GitHub**<br>
Guardar todo mi código y documentar el progreso, para tener portfolio.

<br>

### Herramientas que uso

VirtualBox · Debian · Windows Terminal · Git · GitHub  
**Próximamente:** Ansible · Terraform · Proxmox VE

<br>

## ¿Por qué este proyecto?

Quiero pasar de instalar todo a mano a hacerlo con código, como se hace en empresas.

</div>

Paso 1: Descargar e instalar VirtualBox: https://www.virtualbox.org/

<img width="1912" height="834" alt="Captura de pantalla 2026-06-05 023133" src="https://github.com/user-attachments/assets/f32ec28f-e79c-460d-91dd-b7564d9929cd" />

Paso 2: Descargar el sistema operativo: https://www.debian.org/download

<img width="1750" height="668" alt="Captura de pantalla 2026-06-05 022952" src="https://github.com/user-attachments/assets/1202d04a-b70f-4560-8128-e0d341bd5e43" />

Paso 3: Vamos a crear nuestra máquina virtual.

Arriba a la izquierda, pulsa Nueva

Nombre: lab-1

Tipo: Linux

Versión: Debian (64-bit) → Siguiente

Memoria dejar en 2048 MB (2 GB) → Siguiente

Crear un disco duro virtual ahora → Crear

Tipo: VDI → Siguiente

Reservado dinámicamente → Siguiente

Tamaño: 20 GB → Crear

ISO

Selecciona lab-1 → Configuración → Almacenamiento

En "Controlador IDE", clic en el disco vacío → a la derecha, icono de CD → Elegir archivo de disco

Busca tu debian-13...-netinst.iso en Descargas → Abrir → Aceptar

Pulsa Iniciar. Verás el instalador de Debian en texto.



En creación...
