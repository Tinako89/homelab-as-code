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

Seleccionamos nuestro idioma.

<img width="800" height="671" alt="Captura de pantalla 2026-06-05 202302" src="https://github.com/user-attachments/assets/82f989f3-55a9-4290-8fea-a011c8187390" />

Ubicación y zona horaria.

<img width="800" height="671" alt="Captura de pantalla 2026-06-05 202345" src="https://github.com/user-attachments/assets/0d895aaa-6670-45a6-9048-13783158579c" />

idioma de nuestro teclado.

<img width="798" height="671" alt="Captura de pantalla 2026-06-05 202429" src="https://github.com/user-attachments/assets/dab749b0-9bec-491a-a692-9e2a86b5338d" />

Nombre de la máquina.

<img width="799" height="672" alt="Captura de pantalla 2026-06-05 202554" src="https://github.com/user-attachments/assets/14e1d748-c1d8-4b8e-9744-80ce69f07d0a" />

Nombre de dominio lo dejamos en blanco.

<img width="798" height="674" alt="Captura de pantalla 2026-06-05 202624" src="https://github.com/user-attachments/assets/ec1b8adc-8aab-4727-aee0-c7aca3e59f82" />

Contraseña del super usuario root, la que queramos.

<img width="799" height="672" alt="Captura de pantalla 2026-06-05 202712" src="https://github.com/user-attachments/assets/d6d0eb2f-f0a1-478a-b7f4-b59e18602e69" />

Verificamos contraseña del usuario root.

<img width="798" height="675" alt="Captura de pantalla 2026-06-05 202735" src="https://github.com/user-attachments/assets/48092957-f9f1-483a-a477-ad517fce8d93" />

Nombre de nuestro usuario.

<img width="797" height="674" alt="Captura de pantalla 2026-06-05 202814" src="https://github.com/user-attachments/assets/7cba61b6-2712-48b1-a2cc-0e472b375fd1" />

Nombre para la cuenta.

<img width="800" height="673" alt="Captura de pantalla 2026-06-05 202845" src="https://github.com/user-attachments/assets/650fbac5-ed9c-4ffb-b771-8f7ae0ac5590" />

Contraseña de nuestro usuario.

<img width="798" height="672" alt="Captura de pantalla 2026-06-05 202936" src="https://github.com/user-attachments/assets/ed406a82-1a48-4dc4-a286-51b662138c5c" />

Zona horaria deseada.

<img width="799" height="673" alt="Captura de pantalla 2026-06-05 203009" src="https://github.com/user-attachments/assets/6cba2ed2-6897-48ac-81db-8849fe87bd82" />

Partición de discos, en este caso la harémos guiada, utilizar todo el disco.

<img width="796" height="671" alt="Captura de pantalla 2026-06-05 203056" src="https://github.com/user-attachments/assets/e613fcaf-fd8e-41cd-86ea-ff6cb18c0709" />

Elejimos nuestro disco duro.

<img width="798" height="668" alt="Captura de pantalla 2026-06-05 203130" src="https://github.com/user-attachments/assets/b97b31a0-0cd4-47f4-a8a4-c84cc4977a22" />

Todos los ficheros en una partición.

<img width="799" height="668" alt="Captura de pantalla 2026-06-05 203203" src="https://github.com/user-attachments/assets/c36c7997-3a14-453d-ad93-d9f89808e9c3" />


















En creación...
