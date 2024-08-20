# Primer trabajo obligatorio - Desarrollo de Software Seguro

## Integrantes: Jose Ignacio Lavecchia, Franco Robotti.

En este trabajo realizaremos un Write Up acerca del armado de un ambiente de pruebas de aplicaciones, para esto recurrir a la virtualización consideramos que es la mejor opción.

En este tutorial utilizaremos eligiremos virtualBox como máquina virtual y mostraremos los pasos para configurar los proxys de interpretación ZAP y BURP.


### **Requisitos:**

-Instalación de Kali Linux en una máquina virtual(recomendamos virtual box para este tutorial)
-Instalación de un Proxy de interceptación(ZAP o BURP)
-Instalación de docker en la máquina virtual de Kali Linux
-Ejecución de un contenedor con OWASP Juice Shop
-Prueba de la visualización del tráfico con el proxy de interpretación seleccionado.


### **Instalación de Kali Linux en una máquina virtual**

#### Instalación de Virtual Box:

Para esto primero procederemos al sitio web de virtual box https://www.virtualbox.org/

y haremos click a donde dice "Download Virtual Box 7.0"

![image](https://github.com/user-attachments/assets/b54df357-720f-4645-89ee-aca45c278339)

Posterior a esto simplemente nos paramos a donde dice "VirtualBox 7.0.20 platform packages"  y seleccionamos la versión compatible con nuestro sistema operativo.

![image](https://github.com/user-attachments/assets/87eaace4-8ac2-4355-8bfa-4841a304e53e)

#### Instalación de Kali:

Kali es una distribución del Linux, diseñada específicamente para pruebas de seguridad y hacking ético. 

Posee una gran variedad de herramientas preinstaladas que se utilizan para tareas como análisis de vulnerabilidades, pruebas de penetración, y auditorías de seguridad en sistemas informáticos.

Para proceder a instalarlo primero debemos dirigirnos a su sitio web oficial https://www.kali.org/get-kali/

Una vez en el sitio, debemos hacer click la opción de Virtual Machines

![image](https://github.com/user-attachments/assets/c376983f-c9d6-4a8a-988f-f0b18eaf67d0)

Una vez adentro, debemos seleccionar de Maquina Virtual Pre armada de Virtual Box que mas se adapte a nuestro Sistema Operativos ya sea 64 o 32 bits.

![image](https://github.com/user-attachments/assets/41a9fcf1-3b18-4bd0-9d33-15b838ac71f2)




