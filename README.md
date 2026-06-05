# Homelab-as-Code

Mi laboratorio para aprender a ser Sysadmin Junior.

## ¿Qué estoy aprendiendo?
- **Proxmox**: crear máquinas virtuales con VirtualBox dentro de mi PC.
- **Terraform**: escribir una "receta" para crear esas máquinas automáticamente.
- **Ansible**: configurarlas todas a la vez sin entrar una por una.

## ¿Por qué este proyecto?
Quiero pasar de instalar todo a mano a hacerlo con código, como se hace en empresas.

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
