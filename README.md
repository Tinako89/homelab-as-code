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

Idioma de nuestro teclado.

<img width="798" height="671" alt="Captura de pantalla 2026-06-05 202429" src="https://github.com/user-attachments/assets/dab749b0-9bec-491a-a692-9e2a86b5338d" />

Nombre de la máquina.

<img width="799" height="672" alt="Captura de pantalla 2026-06-05 202554" src="https://github.com/user-attachments/assets/14e1d748-c1d8-4b8e-9744-80ce69f07d0a" />

En nombre de dominio lo dejamos en vacio.

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

Nuestra zona horaria.

<img width="799" height="673" alt="Captura de pantalla 2026-06-05 203009" src="https://github.com/user-attachments/assets/6cba2ed2-6897-48ac-81db-8849fe87bd82" />

Partición de discos, en este caso la harémos guiada, utilizar todo el disco.

<img width="796" height="671" alt="Captura de pantalla 2026-06-05 203056" src="https://github.com/user-attachments/assets/e613fcaf-fd8e-41cd-86ea-ff6cb18c0709" />

Elejimos nuestro disco duro.

<img width="798" height="668" alt="Captura de pantalla 2026-06-05 203130" src="https://github.com/user-attachments/assets/b97b31a0-0cd4-47f4-a8a4-c84cc4977a22" />

Todos los ficheros en una partición.

<img width="799" height="668" alt="Captura de pantalla 2026-06-05 203203" src="https://github.com/user-attachments/assets/c36c7997-3a14-453d-ad93-d9f89808e9c3" />

Finalizamos los cambios del particionado.

<img width="801" height="671" alt="Captura de pantalla 2026-06-05 203231" src="https://github.com/user-attachments/assets/9b2213fe-e2bb-4098-847a-cb4c866fd3f2" />

Escribimos los cambios.

<img width="798" height="674" alt="Captura de pantalla 2026-06-05 203310" src="https://github.com/user-attachments/assets/96b51574-3f1b-4e9d-ab09-edeb8f97af75" />

Instalando sistema base...

<img width="800" height="672" alt="Captura de pantalla 2026-06-05 203350" src="https://github.com/user-attachments/assets/50576d34-375b-4bb8-8e5e-b7c1202a0196" />

Aquí decimos que no queremos participar en la encuesta.

<img width="800" height="669" alt="Captura de pantalla 2026-06-05 203544" src="https://github.com/user-attachments/assets/b19dc6ce-b38d-4392-b057-d6ff10389707" />

Instalamos únicamente SSH Server y utilidades del sistema, marcamos y desmarcamos con la barra espaciadora.

<img width="799" height="673" alt="Captura de pantalla 2026-06-05 203739" src="https://github.com/user-attachments/assets/d87c2bcb-65e5-4e4c-bf72-59deb16b463c" />

¿Instalar el GRUB en el arranque principal? decimos que sí.

<img width="795" height="671" alt="Captura de pantalla 2026-06-05 203841" src="https://github.com/user-attachments/assets/c2497b05-8f9b-4765-b38d-52fa7156fbe9" />

Se instalará en nuestro disco duro /dev/sda que es la primera unidad de disco duro.

<img width="795" height="672" alt="Captura de pantalla 2026-06-05 203906" src="https://github.com/user-attachments/assets/dd9ee78c-66bf-4369-be41-3eefbe42d69c" />

Finalizando la instalación...

<img width="797" height="670" alt="Captura de pantalla 2026-06-05 203938" src="https://github.com/user-attachments/assets/788aa6a8-8c3a-4788-a49e-424421697b4e" />

Damos en continuar y se reiniciará el sistema.

<img width="798" height="672" alt="Captura de pantalla 2026-06-05 204005" src="https://github.com/user-attachments/assets/4c8c8a05-6837-4655-9b64-d1dd163696cf" />

Felicidades, acabas de instalar Debian 13 en VirtualBox.

<img width="536" height="276" alt="Captura de pantalla 2026-06-05 204103" src="https://github.com/user-attachments/assets/fb05b81d-38c9-49c3-be96-978a4fbc1b73" />

Con los comandos ``sudo apt update && sudo apt upgrade -y`` Actualizamos la lista de paquetes disponibles y luego instala automáticamente todas las actualizaciones disponibles del sistema.

<img width="655" height="200" alt="Captura de pantalla 2026-06-05 231311" src="https://github.com/user-attachments/assets/5ca230be-a059-4b6c-944c-a6bdb8edda3e" />

Vamos a darle permisos sudo al usuario tinako con el comando ``usermod -aG sudo tinako`` si ese comando falla probar este ``/usr/sbin/usermod -aG sudo tinako`` 

<img width="539" height="110" alt="Captura de pantalla 2026-06-05 232028" src="https://github.com/user-attachments/assets/48b15ed9-82d5-4971-bd05-645e3a23fb47" />

Comprobamos con el comando ``id tinako`` que tenemos los permisos sudo.

<img width="1209" height="157" alt="Captura de pantalla 2026-06-05 232131" src="https://github.com/user-attachments/assets/ef4a50b4-518b-4d96-acf4-d9f1fc4b30d8" />

instalaremos las siguientes herramientas. ssh, curl, vim y net-tools ``sudo apt install -y openssh-server curl vim net-tools``

<img width="903" height="817" alt="Captura de pantalla 2026-06-05 232644" src="https://github.com/user-attachments/assets/6ec4439d-a882-4c2b-8ff3-13de057326a8" />

Apagamos la máquina virtual con el comando ``poweroff`` y configuramos lo siguiente:

En VirtualBox añade la red interna, Selecciona lab-debian-1 → Configuración → Red

Adaptador 1: déjalo en NAT (para internet)

<img width="862" height="498" alt="Captura de pantalla 2026-06-06 004524" src="https://github.com/user-attachments/assets/7ad63088-b83f-42ca-b17c-917b2ff4493c" />

Adaptador 2: marca "Habilitar adaptador de red" 
Conectado a: Adaptador solo-anfitrión
Nombre: VirtualBox Host-Only Ethernet Adapter (o vboxnet0)

<img width="865" height="497" alt="Captura de pantalla 2026-06-06 005035" src="https://github.com/user-attachments/assets/583efc09-a051-4390-959c-0550be326b2e" />

Arrancamos Debian y ponemos la IP fija, entramos como tinako y ``sudo nano /etc/network/interfaces``

<img width="897" height="415" alt="Captura de pantalla 2026-06-06 005431" src="https://github.com/user-attachments/assets/dec7fdfd-b28f-4077-af67-2ebf2ce0a578" />

Añade al final exactamente esto: 

<img width="234" height="114" alt="Captura de pantalla 2026-06-06 005537" src="https://github.com/user-attachments/assets/5314b8f0-1fbe-44e0-a639-f2fc22a91b38" />

Guarda: Ctrl+O, Enter, Ctrl+X

<img width="622" height="415" alt="Captura de pantalla 2026-06-06 010727" src="https://github.com/user-attachments/assets/844b5c44-2829-4efb-bedf-5fa5b4df8d07" />

Reiniciamos la red.

<img width="581" height="183" alt="Captura de pantalla 2026-06-06 010850" src="https://github.com/user-attachments/assets/27c8f2ab-bd60-4521-b92b-ff136d3d38c6" />

Comprobamos las 2 IPs: ``ip -4 a show enp0s8`` y ``ip -4 a show enp0s3``
Todo correcto, Tenemos exactamente lo que tiene un servidor real: una interfaz pública/NAT para salir a internet y una privada para que tú entres.

<img width="979" height="343" alt="Captura de pantalla 2026-06-06 011208" src="https://github.com/user-attachments/assets/ba74787d-e1ac-478e-9201-329a70658a2c" />

Vamos a realizar una prueba final, desde Windows concectarnos por SSH ``ssh tinako@192.168.56.101``

Conectado por SSH desde Windows PowerShell a tu servidor Debian. Exactamente como lo hace un admin en producción con AWS, Azure o un datacenter.

<img width="1115" height="577" alt="Captura de pantalla 2026-06-06 011555" src="https://github.com/user-attachments/assets/ced7eb8b-a8bf-4de3-955a-a9137d1ab05d" />

Lo que acabas de hacer es el paso que separa a los que "instalan Linux" de los que administran servidores.

<img width="371" height="153" alt="Captura de pantalla 2026-06-06 011832" src="https://github.com/user-attachments/assets/64edbea7-46d5-4793-9a2c-376b5c5f07fc" />

Nivel 2: Automatización.
Toca instalar WSL en tu Windows, metemos Ansible, y con UN comando instalamos Nginx en ese Debian y lo dejamos sirviendo una página en http://192.168.56.101.















































En creación...
