# Primer trabajo obligatorio - Desarrollo de Software Seguro

## Integrantes: Jose Ignacio Lavecchia, Franco Robotti.

En este trabajo realizaremos un Write Up acerca del armado de un ambiente de pruebas de aplicaciones, para esto consideramos que recurrir a la virtualización es la mejor opción.

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

![image](https://github.com/user-attachments/assets/700f8a62-cf46-4789-9885-c9087bbbf10e)

![image](https://github.com/user-attachments/assets/75ad4b8f-79a4-4729-a5dd-5968d55df335)


Esto ya nos creará la máquina virtual, por lo que solo debemos inicializarla.

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

### *Instalación de un Proxy de interceptación(ZAP)*
Una vez adentro de nuestra máquina virtual lo que debemos hacer es entrar a la página oficial de ZAP https://www.zaproxy.org/download/

Posteriormente debemos utilizar la versión compatible con nuestro sistema operativo, en nuestro caso Linux, tenemos 2 opciónes, Linux Installer y Linux Package(la más recomendaba y a efectos de este tutorial va a ser Linux Package, esto debido a qué es mucho más "Plug and Play" ya que no debemos instalar los paquetes por nuestra cuenta).

![image](https://github.com/user-attachments/assets/358b845e-9a91-4195-bfaf-7310fce10fa7) 

Después de la instalación, tendremos una archivo comprimido(.zip) el cuál debemos extraer 
![image](https://github.com/user-attachments/assets/d03cf32c-422f-4348-8be4-62c128599acc)

Posteriormente abrimos la terminal y nos dirigimos a nuestro directorio de descargas para después movernos hacia donde tenemos la carpeta extraída del zip.
![image](https://github.com/user-attachments/assets/f29a6a38-2fcf-45bd-9cb1-a36ee3b0d42d)

![image](https://github.com/user-attachments/assets/6b925478-8112-4351-90b7-3cf609fad1e7)

Ejecutamos el comando ./zap.sh en la consola, para así poder abrir directamente el programa ZAP.

![image](https://github.com/user-attachments/assets/764b3b2f-e478-445a-b126-40a75a7210d8)

Una vez dentro, nos dirigimos a el apartado "Quick Start", en le vamos a configurar la URL la cuál va a ser explorada por el navegador(deber la misma URL en la cuál se va a ejecutar la imagen de nuestro contenedor de docker) a efectos de este tutorial, la url escogida será "http://localhost:3000".

Podemos configurar el navegador por defecto de ZAP en donde dice "Explore your Application", en el caso de este tutorial, el navegador escogido será Firefox.
Esto debido a qué Firefox tiene una compatibilidad nativa con ZAP, lo que facilita la configuración de proxies sin extensiónes adiccionales.

![image](https://github.com/user-attachments/assets/8468ae80-94d8-46cf-a470-43b94d386e54)

Ahora vamos a configurar el proxy del navegador, para ello hacemos click en el ícono Firefox dentro de ZAP.

![image](https://github.com/user-attachments/assets/768b19fc-f968-4331-8e4b-6e9078b333c7)

Una vez adentro de nuestro navegador, procedemos a escribir en el buscador "about:config", esto nos permite acceder a la configuración avanzada del navegador.
![image](https://github.com/user-attachments/assets/0e494dc0-cbf9-417a-b8bb-d9f844fc4bbc)

Recibiremos un mensaje de "Proceda con cuidado", posteriormente debemos hacer click en el botón llamado "Accept the Risk and Continue".(recuerda no tocar otras configuraciónes avanzadas sin tener el conocimiento debido a qué puede afectar la perfomance de nuestro navegador dentro de la máquina virtual)
![image](https://github.com/user-attachments/assets/863365d5-c1f6-4464-8680-977d7b3ccb4b)

Posteriormente escribimos "proxy" en el cambio de texto, y nos aseguramos que la opción marcada en azul "network.proxy.allow_hijacking_localhost" esté seteada en true, esto permite que el navegador reenvie tráfico desde y hacia localhost através del proxy, estamos configurando el proxy a nivel de Red.

![image](https://github.com/user-attachments/assets/a2b6d210-3890-4d00-b4d5-8839132ef7f2)

Ahora debemos configurar el acceso a internet de nuestro proxy, para ello hacemos click en las "tres rallas", para luego hacer click en "settings"
![image](https://github.com/user-attachments/assets/289a0bcd-5ece-41e9-ba88-54828fb63cbc)

Procedemos a escribir "proxy" en el buscador, y nos dirigimos al apartado "settings"
![image](https://github.com/user-attachments/assets/7f50a1cc-5e0c-4b98-a0cb-33c9a4557584)

Una vez allí, seleccionamos la opción "Manual proxy configuration", y escribimos "127.0.0.1" esto es el puerto mediante el cuál nuestro navegador va a conectarse a tráficop HTTP, también utilizamos el mismo para HTTPS
![image](https://github.com/user-attachments/assets/bd16f80d-c3a3-4568-8175-8215b356ae00)

![image](https://github.com/user-attachments/assets/d97b874d-78a0-4d91-b970-aabf3d781f77)

![image](https://github.com/user-attachments/assets/99ec7869-1ee9-4fee-8188-85ad15e13faf)




### *Instalación de un Proxy de interceptación(BURP)* --Parte de Franco




