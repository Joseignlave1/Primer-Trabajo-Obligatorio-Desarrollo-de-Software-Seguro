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

Una vez adentro, debemos seleccionar de Maquina Virtual Pre armada de Virtual Box la opción que mas se adapte a nuestro Sistema Operativos ya sea 64 o 32 bits.

![image](https://github.com/user-attachments/assets/41a9fcf1-3b18-4bd0-9d33-15b838ac71f2)

Al completar la instalación, vamos a tener un archivo comprimido(.zip) 

![image](https://github.com/user-attachments/assets/3de38dee-1fee-4a82-bf49-58392779c6bc)

Al extraerlo tendremos varios .amd, en este caso el que necesitamos es el de virtualBox

![image](https://github.com/user-attachments/assets/1d73b0f7-bcc7-46e1-acc2-67a8d45a619a)


#### Inicialización de la Máquina Virtual con Kali

Abrimos Virtual Box, hacemos click en Maquina-Añadir, y seleccionamos nuestro archivo .amd en nuestro escritorio.

Esto ya nos creará la máquina virtual, por lo que solo debemos inicializa.

El usuario por defecto es kali y la contraseña kali

![image](https://github.com/user-attachments/assets/d9792163-138c-4d7e-af2c-fd2f32984640)

#### Configurarle los recursos:

Adiccionalmente podemos configurarle los recursos, para ello hacemos nos dirigimos a Virtual Box, buscamos nuestra máquina virtual y hacemos click en  configuración - Sistema - Placa base.

En este apartado podemos configurarle la memoria RAM(lo recomendado siempre y cuándo tu equipo lo soporte es 4096MB - 4GB)

****![image](https://github.com/user-attachments/assets/db14a967-495d-4ac4-b3a4-a7fd1edb8c9a)

Para configurar la cantidad de núcleos de nuestro procesador que le asignaremos a la máquina virtual nos dirigiremos a  configuración - Sistema - Procesador.

Lo recomendable es 3 núcleos de RAM(siempre y cuándo tu equipo lo soporte)


![image](https://github.com/user-attachments/assets/a5a2ce64-952b-472a-8583-7867b312c61d)


Recuerda que los recursos que asignamos en estas configuración serán consumidos de el hardware de nuestra Máquina, por lo que es recomendable asignarselos con precaución y de una manera adecuada teniendo en cuenta nuestras especificaciónes.




