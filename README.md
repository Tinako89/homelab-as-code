<div align="center">

<img src="https://github.com/user-attachments/assets/28714852-3f70-41c6-8dd6-48e433ddd235" width="100%" alt="Homelab as Code Banner"/>

<br>

# Homelab as Code

<h3>De "clicar en VirtualBox" → a "terraform apply" en producción</h3>

<p><em>Mi bitácora pública aprendiendo sysadmin desde cero. Sin atajos, todo en Git.</em></p>

<p>
  <a href="https://github.com/togurr95/homelab-as-code"><img src="https://img.shields.io/badge/Estado-Activo-success?style=for-the-badge&logo=github"></a>
  <a href="https://www.debian.org/"><img src="https://img.shields.io/badge/Debian-13_Trixie-A81D33?style=for-the-badge&logo=debian&logoColor=white"></a>
  <a href="https://proxmox.com"><img src="https://img.shields.io/badge/Proxmox_VE-9.2-E57000?style=for-the-badge&logo=proxmox&logoColor=white"></a>
  <a href="https://www.virtualbox.org/"><img src="https://img.shields.io/badge/VirtualBox-7.x-183A61?style=for-the-badge&logo=virtualbox&logoColor=white"></a>
</p>
<p>
  <img src="https://img.shields.io/badge/Ansible-Automatización-EE0000?style=for-the-badge&logo=ansible&logoColor=white">
  <img src="https://img.shields.io/badge/Terraform-IaC-7B42BC?style=for-the-badge&logo=terraform&logoColor=white">
  <img src="https://img.shields.io/badge/Docker-Contenedores-2496ED?style=for-the-badge&logo=docker&logoColor=white">
</p>

</div>

---

🎯 ¿Qué estoy aprendiendo?

1. 🧱 Virtualización con VirtualBox
Mi gimnasio personal. Creo, clono y rompo VMs sin miedo antes de dar el salto a Proxmox VE 9.2 en hardware real.

2. 🐧 Debian 13 (Trixie)
Desde cero: instalación minimal, systemd, usuarios y permisos, redes estáticas y hardening básico. La base de todo sysadmin.

3. 🔐 SSH Profesional
Acceso sin GUI desde Windows Terminal + WSL2. Llaves ED25519, sin contraseñas, como en producción.

4. 🤖 Ansible
Automatización idempotente. De apt update a desplegar Docker + Portainer con un solo playbook YAML.

5. 🏗️ Terraform
Infraestructura como Código. Empiezo con el provider de Docker y migro a Proxmox cuando tenga el lab físico.

6. 📦 Git y GitHub
Todo versionado. Cada laboratorio es un commit, cada error es documentación.
## 🛠️ Stack

| Capa | Tecnología | Estado |
| :--- | :--- | :--- |
| **Hipervisor** | Proxmox VE 9.2 (en VM) | ✅ |
| **Lab Local** | VirtualBox 7.x + Host-Only | ✅ |
| **OS** | Debian 13 Trixie | ✅ |
| **Automatización** | Ansible 2.17 | ✅ |
| **IaC** | Terraform 1.9 | ✅ |
| **Contenedores** | Docker + Portainer | ✅ |

## 🗺️ Roadmap 2026

- [x] Repo + VirtualBox + Debian base
- [x] Red 192.168.56.0/24 + SSH con llaves
- [x] Ansible: Nginx, Docker, hardening
- [x] Terraform: primer contenedor `whoami`
- [x] Proxmox VE instalado y accesible
- [ ] **AHORA →** Terraform provider Proxmox
- [ ] Plantilla cloud-init Debian
- [ ] Pi-hole + Traefik + Homarr con código
- [ ] CI/CD con GitHub Actions

---


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

Finalizar los cambios del particionado.

<img width="801" height="671" alt="Captura de pantalla 2026-06-05 203231" src="https://github.com/user-attachments/assets/9b2213fe-e2bb-4098-847a-cb4c866fd3f2" />

Escribimos los cambios.

<img width="798" height="674" alt="Captura de pantalla 2026-06-05 203310" src="https://github.com/user-attachments/assets/96b51574-3f1b-4e9d-ab09-edeb8f97af75" />

Instalando sistema base.

<img width="800" height="672" alt="Captura de pantalla 2026-06-05 203350" src="https://github.com/user-attachments/assets/50576d34-375b-4bb8-8e5e-b7c1202a0196" />

Aquí decimos que no queremos participar en la encuesta.

<img width="800" height="669" alt="Captura de pantalla 2026-06-05 203544" src="https://github.com/user-attachments/assets/b19dc6ce-b38d-4392-b057-d6ff10389707" />

Instalamos únicamente SSH Server y utilidades del sistema, marcamos y desmarcamos con la barra espaciadora.

<img width="799" height="673" alt="Captura de pantalla 2026-06-05 203739" src="https://github.com/user-attachments/assets/d87c2bcb-65e5-4e4c-bf72-59deb16b463c" />

¿Instalar el GRUB en el arranque principal? decimos que sí.

<img width="795" height="671" alt="Captura de pantalla 2026-06-05 203841" src="https://github.com/user-attachments/assets/c2497b05-8f9b-4765-b38d-52fa7156fbe9" />

Se instalará en nuestro disco duro /dev/sda que es la primera unidad de disco duro.

<img width="795" height="672" alt="Captura de pantalla 2026-06-05 203906" src="https://github.com/user-attachments/assets/dd9ee78c-66bf-4369-be41-3eefbe42d69c" />

Finalizando la instalación.

<img width="797" height="670" alt="Captura de pantalla 2026-06-05 203938" src="https://github.com/user-attachments/assets/788aa6a8-8c3a-4788-a49e-424421697b4e" />

Presionamos en continuar y se reiniciará el sistema.

<img width="798" height="672" alt="Captura de pantalla 2026-06-05 204005" src="https://github.com/user-attachments/assets/4c8c8a05-6837-4655-9b64-d1dd163696cf" />

Felicidades, acabas de instalar Debian 13 en VirtualBox.

<img width="536" height="276" alt="Captura de pantalla 2026-06-05 204103" src="https://github.com/user-attachments/assets/fb05b81d-38c9-49c3-be96-978a4fbc1b73" />

Lo primero que vamos a hacer es logear con el usuario root e instalar sudo ``apt install sudo`` nos permitirá ejecutar comandos con permisos de administrador.

<img width="486" height="175" alt="Captura de pantalla 2026-06-07 224829" src="https://github.com/user-attachments/assets/07894cbe-3f3c-4bc5-874f-38627a9b5eae" />

<img width="781" height="449" alt="Captura de pantalla 2026-06-07 224507" src="https://github.com/user-attachments/assets/ed74155d-31ab-483e-996a-bbc448f9ed4e" />

Con los comandos ``sudo apt update && sudo apt upgrade -y`` Actualizamos la lista de paquetes disponibles y luego instala automáticamente todas las actualizaciones disponibles del sistema.

<img width="655" height="200" alt="Captura de pantalla 2026-06-05 231311" src="https://github.com/user-attachments/assets/5ca230be-a059-4b6c-944c-a6bdb8edda3e" />

Vamos a darle permisos sudo al usuario tinako con el comando ``usermod -aG sudo tinako`` o ``/usr/sbin/usermod -aG sudo tinako`` 

<img width="539" height="110" alt="Captura de pantalla 2026-06-05 232028" src="https://github.com/user-attachments/assets/48b15ed9-82d5-4971-bd05-645e3a23fb47" />

Comprobamos con el comando ``id tinako`` que tenemos los permisos sudo.

<img width="1209" height="157" alt="Captura de pantalla 2026-06-05 232131" src="https://github.com/user-attachments/assets/ef4a50b4-518b-4d96-acf4-d9f1fc4b30d8" />

instalaremos las siguientes herramientas. ssh, curl, vim y net-tools ``sudo apt install -y openssh-server curl vim net-tools``

<img width="640" height="68" alt="Captura de pantalla 2026-06-13 203146" src="https://github.com/user-attachments/assets/4f568921-75f7-4c10-836d-ce02dbae5e0b" />

<img width="903" height="817" alt="Captura de pantalla 2026-06-05 232644" src="https://github.com/user-attachments/assets/6ec4439d-a882-4c2b-8ff3-13de057326a8" />

Apagamos la máquina virtual con el comando ``poweroff`` y configuramos lo siguiente:

En VirtualBox añade la red interna, Selecciona lab-debian-1 → Configuración → Red

Adaptador 1: déjalo en NAT (para internet)

<img width="862" height="498" alt="Captura de pantalla 2026-06-06 004524" src="https://github.com/user-attachments/assets/7ad63088-b83f-42ca-b17c-917b2ff4493c" />

Adaptador 2: Marca "Habilitar adaptador de red" 
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

Instalamos WSL con el siguiente comando ``wsl --install -d Ubuntu`` 

<img width="1109" height="621" alt="Captura de pantalla 2026-06-08 232606" src="https://github.com/user-attachments/assets/ee35f181-4ae6-47a3-9f55-878a3dba2ab8" />

Ejecutamos ``wsl -d Ubuntu`` y estaremos dentro.

<img width="507" height="167" alt="Captura de pantalla 2026-06-08 232902" src="https://github.com/user-attachments/assets/fda64c5c-9950-4912-b42d-2693cf295be5" />

Ahora, los 3 comandos que te convierten en automatizador: ``sudo apt update && sudo apt install -y ansible sshpass``
Te pedirá tu contraseña de Ubuntu (la que acabas de crear). Escribe, pulsa Enter. Tardará 1-2 minutos.

<img width="1112" height="619" alt="Captura de pantalla 2026-06-08 233249" src="https://github.com/user-attachments/assets/841e0f82-914c-4eae-b546-3926a774bb38" />

Comprobamos la versión de ansible ``ansible --version`` 

<img width="1083" height="192" alt="Captura de pantalla 2026-06-08 233431" src="https://github.com/user-attachments/assets/f0af42e7-3206-4363-a289-dc69b3d01a48" />

Perfecto. Ahora 3 comandos y Ansible ya habla con tu Debian, En esa misma ventana de Ubuntu (WSL) Crea la llave (pulsa Enter 3 veces):

``ssh-keygen -t ed25519 -N ""`` 

<img width="748" height="429" alt="Captura de pantalla 2026-06-08 233839" src="https://github.com/user-attachments/assets/404ae472-9163-46d9-bae7-fb817f5ca101" />

En esa misma ventana donde acabas de generar la llave, copia y pega: ``ssh-copy-id tinako@192.168.56.101`` hemos dado a tu Debian una copia de tu llave para que ya no te pida contraseña nunca más. Ahora tu Ubuntu y tu Debian se reconocen como "de confianza".

<img width="1106" height="322" alt="Captura de pantalla 2026-06-08 234053" src="https://github.com/user-attachments/assets/2e3da6f4-b45b-49b5-81af-29c917378787" />

Comprobamos una vez más ``ssh tinako@192.168.56.101 "hostname"`` Si te devuelve lab-debian-1 sin pedir contraseña, Ansible ya puede trabajar.

<img width="733" height="85" alt="Captura de pantalla 2026-06-08 234344" src="https://github.com/user-attachments/assets/ac91d7d0-96b4-46e3-af83-284ed805499f" />

Ahora vamos a lo de Ansible de verdad. Solo 2 archivos. Crear el inventario. ``mkdir -p ~/ansible-lab && cd ~/ansible-lab`` y ``nano inventory.ini`` 

<img width="795" height="49" alt="Captura de pantalla 2026-06-08 234552" src="https://github.com/user-attachments/assets/6b260c7b-f18a-4bdd-968a-dfcbba24326b" />

Nos enviará a Nano, copiamos y pegamos lo siguiente: ``[web]
lab1 ansible_host=192.168.56.101 ansible_user=tinako``
Guarda: Ctrl+O, Enter, Ctrl+X

<img width="698" height="349" alt="Captura de pantalla 2026-06-08 234716" src="https://github.com/user-attachments/assets/399d7b51-8b3e-46c8-9b29-b3e52bb60d6c" />

Probamos Asinble ``ansible -i inventory.ini web -m ping``
El pong lo genera Debian por dentro y Ansible te lo trae a Ubuntu para confirmar que SSH y Python funcionan.

<img width="1114" height="345" alt="Captura de pantalla 2026-06-08 234902" src="https://github.com/user-attachments/assets/647e4560-f2e5-41f9-a3aa-92ce9af5461b" />

Siguiente paso real del curso: instalar Nginx en Debian con 1 playbook, sin tocar la VM.

Creamos el playbook con ``cd ~/ansible-lab`` y ``nano web.yml``

<img width="459" height="81" alt="Captura de pantalla 2026-06-08 235543" src="https://github.com/user-attachments/assets/f91a767c-d910-4fc6-9bcb-1f7f16e5bd40" />

Dentro de nuestro nano .yml copiamos y pegamos el siguiente código (Conecta a Debian, instala Nginx con apt y lo deja arrancado y activado al inicio.)
Guarda: Ctrl+O, Enter, Ctrl+X
      
<img width="699" height="431" alt="Captura de pantalla 2026-06-08 235732" src="https://github.com/user-attachments/assets/a1802fc7-9ac5-4983-b5e3-6b3fc94e2de2" />

Ejecutamos ``ansible-playbook -i inventory.ini web.yml -K``y pon la contraseña de Debian cuando te la pida. lo que hará este comando es: Lee web.yml, se conecta a Debian por SSH usando inventory.ini, y ejecuta las tareas en orden.

<img width="1107" height="413" alt="Captura de pantalla 2026-06-09 000339" src="https://github.com/user-attachments/assets/c63bd175-17fd-45ee-8bba-5006144e1cd8" />

Ahora prueba en tu Windows: abre el navegador y ve a ``http://192.168.56.101`` Deberías ver la página "Welcome to nginx!"

<img width="645" height="363" alt="Captura de pantalla 2026-06-09 000505" src="https://github.com/user-attachments/assets/5a7d4b93-8fa1-4ecb-8492-e584ee85b3c2" />

Acabas de hacer con Ansible lo que normalmente harías a mano en Debian:
Y todo con un solo comando. Eso es automatización. El "No seguro" es normal, es http sin certificado. No pasa nada en tu lab.

    conectaste desde Ubuntu
    instalaste Nginx
    lo dejaste corriendo

Lo siguiente que vamos a hacer es "Haz que Ansible despliegue TU página, no la de Nginx." Será una página muy básica de prueba.

Creamos el archivo `echo "<h1>Hola Ansible</h1>" > ~/ansible-lab/index.html` 

<img width="890" height="349" alt="Captura de pantalla 2026-06-09 003056" src="https://github.com/user-attachments/assets/46c60c30-6850-459b-91c7-0973905561fd" />

Editamos web.yml con nano  con el siguiente código ``nano ~/ansible-lab/web.yml``  

<img width="806" height="267" alt="Captura de pantalla 2026-06-09 003225" src="https://github.com/user-attachments/assets/6bb3f962-bf88-42c6-9659-dae688778005" />

Y ejecutamos ``ansible-playbook -i inventory.ini web.yml -K`` 
Explicación: Ansible entró a lab1, no reinstaló Nginx porque ya estaba, solo copió tu "Hola Ansible" a la web y confirmó que el servicio sigue activo.

<img width="1105" height="475" alt="Captura de pantalla 2026-06-09 003352" src="https://github.com/user-attachments/assets/feb2c89f-1ddd-44ec-9195-c52d8d522666" />

Resultado: si ahora recargas ``http://192.168.56.101`` ya no ves "Welcome to nginx", ves "Hola Ansible".

<img width="780" height="268" alt="Captura de pantalla 2026-06-09 003639" src="https://github.com/user-attachments/assets/c53b8087-e240-4ae6-aca1-eb7aae36f365" />

Toca el turno de Usar variables (que el título cambie según el servidor)
Así verás cómo Ansible personaliza cada servidor sin copiar archivos a mano.

Edita index.html: ``nano ~/ansible-lab/index.html`` Guarda igual (Ctrl+O, Enter, Ctrl+X).

<img width="845" height="281" alt="Captura de pantalla 2026-06-09 025938" src="https://github.com/user-attachments/assets/bce8419c-0066-42cf-93a4-2387dc4a1a80" />

Ejecutamos el siguiente comando ``sed -i 's/- copy:/- template:/' web.yml`` Para que Ansible no copie el texto tal cual, sino que lo rellene con el nombre de la máquina.

<img width="680" height="129" alt="Captura de pantalla 2026-06-09 030728" src="https://github.com/user-attachments/assets/951596eb-aa6c-468f-849e-ead54ab8184d" />

Comprobamos que cambió ``cat web.yml`` 

<img width="582" height="176" alt="Captura de pantalla 2026-06-09 030911" src="https://github.com/user-attachments/assets/faaf1f5a-370c-48c8-94e7-b0ad690c2225" />

Ahora el paso final ``ansible-playbook -i inventory.ini web.yml -K`` pon la contraseña cuando te la pida, y espera al PLAY RECAP.

<img width="1112" height="469" alt="Captura de pantalla 2026-06-09 031245" src="https://github.com/user-attachments/assets/9b7102e8-d223-4bd2-8ef4-e21f4525a8be" />

Abre el navegador con la siguiente URL ``http://192.168.56.101``

<img width="660" height="221" alt="Captura de pantalla 2026-06-10 054502" src="https://github.com/user-attachments/assets/f6f78c80-1078-48cb-98c7-b225ef812d02" />

Lo que acabas de hacer en una línea:

    Conectaste desde el controlador a lab1 por SSH
    Instalaste nginx
    Subiste una plantilla y la personalizaste
    Arrancaste el servicio
    
Ahora vamos con el segundo playbook, que es el que deja tu Debian con usuario, firewall y updates automáticos.

PASO 1: Abre PowerShell y escribe ``wsl`` crea la carpeta de trabajo: ``mkdir -p ~/homelab`` y ``cd ~/homelab``

<img width="945" height="283" alt="Captura de pantalla 2026-06-11 191609" src="https://github.com/user-attachments/assets/fd1fdb71-c424-424c-9431-66d5ae5113bd" />

PASO 2: Crea el inventario (le dice a Ansible dónde está tu VM)

<img width="943" height="230" alt="Captura de pantalla 2026-06-11 192356" src="https://github.com/user-attachments/assets/1d8d59fa-af6f-4a90-95ba-a7e4b44089bf" />

Creamos el playbook

<img width="816" height="863" alt="Captura de pantalla 2026-06-11 193159" src="https://github.com/user-attachments/assets/e4bcadfe-cb96-4806-91bc-ca0d9cd3ee18" />

Comprobamos con ``ls`` y ``cat`` 

<img width="608" height="154" alt="Captura de pantalla 2026-06-11 193514" src="https://github.com/user-attachments/assets/6e85e634-f852-4e54-852c-3b53dfe5325d" />

Generamos la llave.

<img width="945" height="144" alt="Captura de pantalla 2026-06-11 194041" src="https://github.com/user-attachments/assets/e78b334f-3a96-4207-b7fb-56082320a2bf" />

La llave ya estaba instalada antes, no tenemos que hacer na más aquí.

<img width="945" height="146" alt="Captura de pantalla 2026-06-11 194317" src="https://github.com/user-attachments/assets/375776d3-2407-4f56-a24a-bef370a4a9ca" />

En la siguiente imágen le preguntaste a Ansible: "¿puedes entrar por SSH en mi Debian (lab1) usando la agenda inventory.ini?" y te respondió "pong" = sí puedo.

<img width="799" height="145" alt="Captura de pantalla 2026-06-11 194407" src="https://github.com/user-attachments/assets/f3ae6c60-736a-457b-910f-18061783844a" />

Último comando de la Fase 2, pégalo y dale Enter, lanzaste el playbook con -K, metiste la contraseña, y Ansible configuró tu Debian sin errores (failed=0).

<img width="956" height="665" alt="Captura de pantalla 2026-06-11 194816" src="https://github.com/user-attachments/assets/dac19711-f04b-4af8-8c9e-b0492b7beebb" />

<img width="626" height="234" alt="Captura de pantalla 2026-06-11 195022" src="https://github.com/user-attachments/assets/fb9e66ff-6044-4b13-94fd-e1a236496665" />

Fase 3: instalar Docker + Portainer con Ansible (para gestionar contenedores desde web)
Objetivo: que Ansible instale Docker en tu Debian y levante Portainer, para que gestiones contenedores desde el navegador en https://192.168.56.101:9443

Editamos el siguiente .yml con nano ``nano docker.yml`` 

<img width="645" height="874" alt="Captura de pantalla 2026-06-11 201452" src="https://github.com/user-attachments/assets/ca21457c-6c73-4f1d-bf04-eb522590c983" />

Ejecutamos ``ansible-playbook -i inventory.ini docker.yml``

<img width="949" height="543" alt="Captura de pantalla 2026-06-11 201541" src="https://github.com/user-attachments/assets/1fb6bc85-8bcb-4e78-9f4f-496b7d7e472b" />

Abrimos puertos.

<img width="954" height="172" alt="Captura de pantalla 2026-06-11 202059" src="https://github.com/user-attachments/assets/5c04058f-711a-472b-99fa-3693235b3db2" />

Comprueba que Portainer está corriendo.

<img width="937" height="120" alt="Captura de pantalla 2026-06-11 202203" src="https://github.com/user-attachments/assets/5a34e1e3-5211-486c-9547-487abb1f5b35" />

Ya abriste los puertos con UFW ahora comprobamos la siguiente url: ``https://192.168.56.101:9443``

<img width="899" height="836" alt="Captura de pantalla 2026-06-11 202402" src="https://github.com/user-attachments/assets/717fe1b8-77ca-4ae3-83ab-5c61d1df84ec" />

Portainer está vivo en https://192.168.56.101:9443

<img width="518" height="114" alt="Captura de pantalla 2026-06-11 202531" src="https://github.com/user-attachments/assets/90aff777-ba4f-4dd0-8ab8-3b28eacb7228" />

Vamos con Terraform, Terraform es un cuaderno de planos para tu infraestructura.

Tú escribes en un archivo de texto cómo quieres que sea tu homelab: "una VM Debian, con Docker instalado, y con tres contenedores corriendo". No le dices los pasos, solo el resultado final.

Terraform lee ese plano y hace tres cosas:

    Mira lo que hay ahora (gracias a un archivo de estado que guarda). Sabe si ya tienes el contenedor o no.

    Compara con lo que quieres. Si falta algo, lo crea. Si sobra algo, lo borra. Si cambió algo, lo actualiza.

    Funciona con todo. No es solo para la nube. Tiene "conectores" para VirtualBox, Proxmox, Docker, AWS, Cloudflare... Cambias el conector y el mismo lenguaje te sirve.

Diferencia con Ansible:

    Ansible es para configurar lo que ya existe: instalar paquetes, poner usuarios, abrir puertos.
    Terraform es para decidir qué existe: crear la VM, crear el contenedor, crear la red.

Por eso se usan juntos: Terraform levanta las piezas, Ansible las deja listas por dentro.

En tu caso, ya no tendrías que entrar a Portainer a clicar. Cambias una línea en el plano ("añadir Pi-hole"), le das a aplicar, y Terraform se encarga de que Pi-hole aparezca en tu Debian exactamente como lo escribiste. Si lo borras del plano, desaparece.

PASO 1: Instalar Terraform ``sudo apt install terraform -y`` 

<img width="953" height="350" alt="Captura de pantalla 2026-06-12 230849" src="https://github.com/user-attachments/assets/3366f1e6-05d3-4a29-9fbe-2a4dd95f0abd" />

Comprobamos la versión.

<img width="395" height="63" alt="Captura de pantalla 2026-06-12 230947" src="https://github.com/user-attachments/assets/4ffcdcd3-1c0c-4b44-8104-35b877d0f109" />

Abrrir el puerto 8080 en lab1 ``ansible lab1 -i ~/homelab/inventory.ini -b -m shell -a "ufw allow 8080/tcp"``

<img width="909" height="82" alt="Captura de pantalla 2026-06-12 231117" src="https://github.com/user-attachments/assets/d9827c34-9dd9-4b8f-90c3-3449a87d5e5a" />

Crea tu primer proyecto Terraform, creamos directorio ``mkdir -p ~/terraform-homelab`` ``cd ~/terraform-homelab`` y editamos con nano ``nano main.tf`` 

<img width="508" height="85" alt="Captura de pantalla 2026-06-12 231343" src="https://github.com/user-attachments/assets/11565bf8-1ce7-4fa3-99d2-0333bff3d2a7" />

Guarda: Ctrl+O → Enter → Ctrl+X

<img width="1231" height="713" alt="Captura de pantalla 2026-06-12 231459" src="https://github.com/user-attachments/assets/001c0d4d-cb6c-4235-9d00-0ac26c6c7b16" />

Estás en ~/terraform-homelab. Inicializa y lanza ``terraform init`` Descargará el plugin de Docker

<img width="828" height="533" alt="Captura de pantalla 2026-06-12 231622" src="https://github.com/user-attachments/assets/1c1d0217-929b-445b-b361-8926ab6a6390" />

Luego ejecuta ``terraform apply -auto-approve`` Al final: Apply complete! Resources: 2 added

<img width="1522" height="1026" alt="Captura de pantalla 2026-06-12 231744" src="https://github.com/user-attachments/assets/9d329e0f-e522-426e-a3fc-59c6070fcc4c" />

<img width="1399" height="948" alt="Captura de pantalla 2026-06-12 231812" src="https://github.com/user-attachments/assets/52aee020-b254-4959-ad4f-4fe56f16b014" />

Comprobamos con el siguiente comando ``ansible lab1 -i ~/homelab/inventory.ini -m shell -a "docker ps"``

Mira tu docker ps:

    whoami → 0.0.0.0:8080->80/tcp Up 2 minutes
    Creado por Terraform hace 2 minutos, no por Portainer

Has desplegado tu primera infraestructura como código. Ya no tocaste Portainer, solo un archivo .tf.

<img width="1889" height="269" alt="Captura de pantalla 2026-06-12 232005" src="https://github.com/user-attachments/assets/bc4d0c9e-344e-40b0-9b21-f4e8b801ed00" />

Prueba final, abre tu navegador en windows: http://192.168.56.101:8080

Esa página que ves es tu contenedor whoami creado 100% con Terraform, desde tu Ubuntu, sin tocar Portainer.

    Hostname: 63473407e917 → es el ID que salía en tu docker ps
    RemoteAddr: 192.168.56.1 → eres tú desde Windows
    Puerto 8080 abierto por la regla UFW que pusimos con Ansible

Ya tienes el ciclo completo: Ansible prepara la VM → Terraform despliega la app → tú la consumes.

<img width="776" height="394" alt="Captura de pantalla 2026-06-12 232235" src="https://github.com/user-attachments/assets/d1cfd145-31b6-4a09-8043-730c8f9d80bf" />

Instalar Proxmox en VirtualBox 

Nombre: pve
Tipo: Linux → Debian (64-bit)
Imágen ISO: La que hemos descargado.


<img width="784" height="582" alt="Captura de pantalla 2026-06-18 191109" src="https://github.com/user-attachments/assets/eee84509-19a5-4c1a-9064-2fb082b00db6" />

CPU: 2 cores mínimo, marca "Habilitar PAE/NX"
RAM: 4096 MB mínimo (8192 ideal)

<img width="781" height="581" alt="Captura de pantalla 2026-06-18 191337" src="https://github.com/user-attachments/assets/68c2a6c4-e46b-4c3a-b6f6-5579fbfc65c4" />


Disco: Crear VDI → 32 GB mínimo (dinámico)

<img width="785" height="581" alt="Captura de pantalla 2026-06-18 191433" src="https://github.com/user-attachments/assets/be518c73-744c-458f-9f5f-2d915cb25e1a" />

Instalacion Proxmox VE

Iniciamos y elegimos la opción de instalacion gráfica.

<img width="1024" height="836" alt="Captura de pantalla 2026-06-18 191617" src="https://github.com/user-attachments/assets/bd99bca5-4f9b-4ec1-b521-716256d820ff" />

Te mostrará el espacio de disco duro ``sda - 32GB``

<img width="1280" height="853" alt="Captura de pantalla 2026-06-18 191839" src="https://github.com/user-attachments/assets/915e75ac-8561-49a2-914f-b4a3ab4523a4" />

Seleccionamos nuestro páis, zona horario y el idioma de nuestro teclado.

<img width="1283" height="853" alt="Captura de pantalla 2026-06-18 192005" src="https://github.com/user-attachments/assets/af5ab6d4-3bb9-4b53-980a-3685e4b97bf2" />

Contraseña y nuestro email.

<img width="1285" height="842" alt="Captura de pantalla 2026-06-18 192054" src="https://github.com/user-attachments/assets/1678291b-afcf-44ae-900b-c83c1197b6fc" />

Configuracion de red, Ponlo así para que esté en tu misma red que lab1

<img width="1280" height="851" alt="Captura de pantalla 2026-06-18 192439" src="https://github.com/user-attachments/assets/95b868d2-3474-4986-b044-3687d14aed2d" />

Comenzará la instalación.

<img width="1281" height="850" alt="Captura de pantalla 2026-06-18 192531" src="https://github.com/user-attachments/assets/85c6d6eb-651d-41b7-83ff-c5c2daa2a90f" />

Una vez instalado se reiniciará automaticamente, iniciamos y "extraemos el disco" Dispositivos → Unidades ópticas → Quitar disco de la unidad virtual

<img width="1028" height="843" alt="Captura de pantalla 2026-06-18 192926" src="https://github.com/user-attachments/assets/9f373a4f-b82f-4829-8b03-3d8d72ba99e8" />

Apagamos y volvemos a encender, Proxmox VE 9.2 ya está instalado, arrancado y con red funcionando en tu VirtualBox.

<img width="871" height="501" alt="Captura de pantalla 2026-06-18 193137" src="https://github.com/user-attachments/assets/351c734a-8e94-4ac8-8ca1-c45a0bf8dcb2" />

Antes de acceder a Promox desde el navegador web, en red ponemos adaptador puente para la comunicacion de las dos máquinas "lad-debian-1" y "pve"

<img width="866" height="505" alt="Captura de pantalla 2026-06-18 194415" src="https://github.com/user-attachments/assets/32f29502-c50f-4eb7-9226-423034626998" />

Ahora si, vamos al navegador web https://192.168.56.10:8006 

<img width="1909" height="910" alt="Captura de pantalla 2026-06-18 194538" src="https://github.com/user-attachments/assets/ceaa8c48-f0b5-4059-bf94-71190c329aa0" />

Entramos con usuario root y contraseña que pusiste en la instalacion de Proxmox.

<img width="1916" height="911" alt="Captura de pantalla 2026-06-18 194805" src="https://github.com/user-attachments/assets/64e6674c-9ed8-44a2-9444-d498279ba451" />

<img width="1918" height="912" alt="Captura de pantalla 2026-06-18 194933" src="https://github.com/user-attachments/assets/7f3200c1-8afe-4dc0-a43b-46d3093fc28c" />

<div align="center">

</div>













































 











      





















































