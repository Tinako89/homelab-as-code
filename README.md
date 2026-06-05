<div align="center">

<img width="1440" height="816" alt="homelab_cover_v3_44522697" src="https://github.com/user-attachments/assets/28714852-3f70-41c6-8dd6-48e433ddd235" />


### De instalar a mano → a automatizar como en producción


*Proyecto personal para aprender administración de sistemas desde cero*

[![Status](https://img.shields.io/badge/Estado-En%20construcción-yellow)](https://github.com/togurr95/homelab-as-code)
[![Linux](https://img.shields.io/badge/OS-Debian%2013-red)](https://debian.org)
[![Made with](https://img.shields.io/badge/Made%20with-VirtualBox-blue)](https://virtualbox.org)

</div>

---

## 🎯 ¿Qué estoy aprendiendo?

> No es un laboratorio perfecto, es mi cuaderno de prácticas.

**1. Virtualización con VirtualBox**
Primero aprendo a crear máquinas virtuales en mi PC. Es el gimnasio antes de saltar a Proxmox VE en un servidor real.

**2. Linux Debian 13 (Bookworm/Trixie)**
Instalación mínima, gestión por terminal, usuarios, permisos, systemd y redes. La base de cualquier sysadmin.

**3. Acceso remoto con SSH**
Conectarme desde Windows Terminal sin usar la pantalla de VirtualBox, como se trabaja en empresas.

**4. Ansible**
Automatizar configuración: instalar paquetes, crear usuarios y desplegar servicios con playbooks en YAML.

**5. Terraform**
Definir infraestructura como código. Empezaré con VirtualBox y migraré a Proxmox cuando tenga hardware.

**6. Git y GitHub**
Versionar todo. Cada cambio es un commit, cada práctica es documentación.

## 🛠️ Stack actual

| Capa | Herramienta | Estado |
| :--- | :--- | :--- |
| Virtualización | **VirtualBox 7.x** | ✅ En uso |
| Sistema Operativo | **Debian 13** | ✅ Instalando |
| Terminal | Windows Terminal + SSH | ✅ |
| Control de versiones | Git + GitHub | ✅ |
| Configuración | **Ansible** | 🔜 Próximo |
| IaC | **Terraform** | 🔜 Próximo |
| Hipervisor real | **Proxmox VE** | 🔜 Fase 2 |

## 🗺️ Roadmap

- [x] Crear repositorio y documentación
- [x] Instalar VirtualBox
- [x] Primera VM Debian (lab-1)
- [ ] Configurar SSH y acceso sin contraseña
- [ ] Primer playbook Ansible: actualizar sistema
- [ ] Segundo playbook: instalar Nginx
- [ ] Migrar a Terraform para crear VMs
- [ ] Instalar Proxmox en hardware dedicado

Paso 1: Descargar e instalar VirtualBox: https://www.virtualbox.org/

<img width="1912" height="834" alt="Captura de pantalla 2026-06-05 023133" src="https://github.com/user-attachments/assets/f32ec28f-e79c-460d-91dd-b7564d9929cd" />

Paso 2: Descargar el sistema operativo: https://www.debian.org/download

<img width="1750" height="668" alt="Captura de pantalla 2026-06-05 022952" src="https://github.com/user-attachments/assets/1202d04a-b70f-4560-8128-e0d341bd5e43" />

Paso 3: Vamos a crear nuestra máquina virtual.

Arriba a la izquierda, pulsa Nueva.

<img width="782" height="701" alt="Captura de pantalla 2026-06-05 200434" src="https://github.com/user-attachments/assets/4c1bddea-223d-4eba-957a-6cb31f81d180" />

Nombre: lab-debian-1
Tipo: Linux.
ISO: La imágen ISO que hemos descargado anteriormente.
Marcar el cuadrito "Omitir isntalación desatendida"
Versión: Debian (64-bit)

<img width="869" height="640" alt="Captura de pantalla 2026-06-05 202053" src="https://github.com/user-attachments/assets/7a0f43e4-a920-4005-9e69-311c3ec399c2" />

Memoria dejar en 2048 MB, añade si quieres dos núcleos.

<img width="1028" height="585" alt="Captura de pantalla 2026-06-05 192227" src="https://github.com/user-attachments/assets/cf490cd9-693b-441c-93d0-22d8a12d3e9b" />

Crear un disco duro virtual ahora.
Tipo: VDI. 
Reservado dinámicamente. 
Tamaño: 20 GB

<img width="1028" height="580" alt="Captura de pantalla 2026-06-05 192318" src="https://github.com/user-attachments/assets/8a994636-eeaa-4bf6-aa7f-a008a4eeb9e2" />

Damos click en el botón de iniciar.

<img width="995" height="775" alt="Captura de pantalla 2026-06-05 193952" src="https://github.com/user-attachments/assets/f74133ec-8753-46de-b8ea-2ee7a7bd0f82" />

Paso 4: Instalar Debian. 

Elegimos la segunda opción, NO instalaremos por interfaz gráfica.

<img width="638" height="549" alt="Captura de pantalla 2026-06-05 202206" src="https://github.com/user-attachments/assets/412ea7f9-35ad-45e3-8c0e-221cc09d418e" />







En creación...
