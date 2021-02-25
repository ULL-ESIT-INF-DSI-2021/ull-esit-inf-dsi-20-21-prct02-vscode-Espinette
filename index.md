# INFORME PRACTICA 2
## Instalación y configuración de Visual Studio Code
### ALBERTO RIOS DE LA ROSA
### alu0101235929@ull.edu.es

### INTRODUCCIÓN

En esta práctica aprenderemos distintas funcionalidas del **Visual Studio Code**, instalando y configurandolo para realizar futuro trabajos, donde nos conectaremos por `ssh`a nuestra máqina virtuales, además añadiremos varias extensiones entre ella una que nos permita crear sesiones colaborativas y realizaremos nuestro prtimer pequeño programa en TypeScript.

### ELABORACIÓN POR PASOS 

#### 1. Instalar Visual Studio Code

Este paso solo es necesario que lo hagan aquellos que no tengan instalado [Vs code](https://code.visualstudio.com/), por mi parte yo ya lo tenía instalado pero aquellos que tengan que realizarlo deben hacer uso del siguiente comando:

```bash
  alberto@ubuntu:~$ sudo apt install code
```

En caso de que no puedas prueba a hacer uso de snap para su instalación:

```bash
  alberto@ubuntu:~$ sudo snap install code --classic
```

#### 2. Configurar Visual Studio para conectarnos con SSH a nuestra máquina virtual

Es imprescindible tener la [práctica 1](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Espinette/), en caso de no tenerla, debemos volver y realizarla. Además siempre que trabajemos con nuestra máquina virtual del Iaas debemos conectarnos a través de la VPN de la ULL.

Ya teniendo hecho esto, debemos abrir el VSCode, e instalar la extensión ***Remote-SSH*** para que nos permita conectarnos a nuestra terminal de la máquina virtual desde el visual. Ya instalado la extensión usando `Ctrl + Shift + P`abriremos una paleta de comando en la que escribiremos **SSH** y entre todas las opciones pulsaremos en la de **Connect to Host...**. En el caso de haber seguido correctamente todos los pasos en la [práctica 1](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-Espinette/) nos debe salir el nombre que asignamos a nuestra máquina virtual en el menu principal, como es en mi caso. Pulsaremos sobre el nombre y se nos abrirá una ventana nueva estando ya conectada por SSH con nuestra máquina.

Para estar seguro de que estamos bien conectado a nuestra máquina virtual, vemos que en la parte inferior izquierda de la pestaña tendremos en verde el nombre de la máquina virtual en la que nos encontramos. Pero ya para estar seguro abrimos una nueva terminal, que se debería abrir con el formato prompt que habiamos realizado en la practica uno ejecutaremos el comando `hostname`y nos responderá con el nombre de nuestra máquina:

```bash
  [~()]$hostname
  iaas-dsi2
```

#### 3. Sesion colaborativa con Visual Studio Live


Visual Studio además nos permite realizar trabajos colaborativos en tiempo rea, esto es posible gracias a la herramienta Visual Studio Live Share. Para esto debemos instalar la extensión **Live Share Extension Pack**, esta estrá disponible en el mismo lugar donde nos instalamos la extensión para poder conectarnos por SSH. Hay que recordar que todas las extensiones que se instalen deben realizarce estando conectados a la máquina virtual, ya que estas extensiones solo se instalán es ese visual. Si quisieramos instalar esa extensión el Visual de nuestra máquina normal, debemos hacerlo fuera de conexión de la máquina remota.

Ya con la extensión instalada probamos la extensión creeando un archivo cualquiera, y en la parte inferior izquierda de la pestaña encontraremos un boton que dice *live share* y nos pedirá que para poder compartir en live un proyecto enlacemos nuestra cuenta de visual con la del github para que esten sincronizadas, una vez realizado veremos que abajo a la izquierda tendremos un apartado llamado session details, donde desde ahí nos dejará ver los detalles de la sesión, iniciar una llamada de audio con los participantes, invitar a nuevos miembros.... 

Podremos obtener mas información sobre la documentación de Visual Studio Live Share en el siguiente [enlace](https://docs.microsoft.com/en-us/visualstudio/liveshare/).

#### 4. Nuestro primer proyecto TypeScript

Primero debemos instalar una serie de extension como ya hemos hecho con anterioridad, por un lado tenemos **VIM** que es un editor de texto que todos conocerán ya y **ESLint** que sirve para realizar comprobaciones sobre fichero con código fuente en JavaScript y TypeScript

Recuerden que siempre estamos conectado a nuestra máquina remota desde visual, ahora abriremos una nueva terminal e instalaremos el compilador de Typrscript, ejecutando:

```bash
[~()]$npm install --global typescript

added 1 package, and audited 2 packages in 2s

found 0 vulnerabilities
[~()]$tsc --version
Version 4.1.3
```

Ahora crearemos los ficheros y directorios necesarios:

```bash
  # Observamos si estamos en la carpeta personal de nuestra máquina remota
  
  [~()]$pwd
  /home/usuario
  
  # Creamos el directorio de nuestro programa "Hello world" y nos ubicamos en el mismo
  
  [~()]$mkdir hello-world
  [~()]$cd hello-world/
  
  # A partir de este comando se nos crea un fichero denominado 'package.json' en el que podemos observar que su contenido se encontrarán las depenedencias de desarrollo y ejecutará el proyecto a modo de paquetes de los que depende el proyecto actual
  
  [~/hello-world()]$npm init --yes
  Wrote to /home/usuario/hello-world/package.json:

  {
    "name": "hello-world",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC"
  }

  # Mostramos el contenido del directoria actual
  
  [~/hello-world()]$ls -lrtha
  total 12K
  drwxr-xr-x 26 usuario usuario 4,0K feb  9 18:46 ..
  drwxrwxr-x  2 usuario usuario 4,0K feb  9 18:48 .
  -rw-rw-r--  1 usuario usuario  225 feb  9 18:48 package.json
  [~/hello-world()]$

```

Ahora abrimos el directorio `Hello-world`creado en Vscode donde podremos ver el contenido de este. Para esto vamos al menu File y seleccionamos la opcion Open folder..., donde se nos mostrarán todas las carpetas seleccionando la deseada.

Ya abierto el directorio crearemos un nuevo fichero dentro de este denominado **tsconfig.json** donde se especificarán las opciones del compilador TypeScript. El fichero deber indluir:

```bash
[~/hello-world()]$cat tsconfig.json 
{
  "compilerOptions": {
    "target": "ES2018",
    "outDir": "./dist",
    "rootDir": "./src",
    "module": "CommonJS"
  }
}
```

Ahora añadiremos un fichero de códgio de TypeScripyt, pero antes debemos realizar los siguientes pasos desde la carpeta de nuestro trabajo, en este caso el directorio hello-world:

```bash
  #Creamos el directorio 'src', que contendrá el código fuente escrito en TypeScript
  [~/hello-world()]$mkdir src
  
  # Nos movemos al directorio 'src'
  [~/hello-world()]$cd src
  
  # Creamos el fichero 'index.ts' vacío
  [~/hello-world/src()]$touch index.ts
```

Abriremos el fichero index.ts creado y le añadimos estás lineas:

```bash
let myString: string = "Hola Mundo";
console.log(myString);
```
Y en la terminal ejecutamos el comando `tsc`, esto crerá un directorio dist, que tendrá un fichero index.js, si mostramos el contenido de ese fichero será el mismo que el de tipo TypeScript pero traducido a JavaScript. Ahora ejecutamos el código Javascript:

```bash
[~/hello-world()]$node dist/index.js
Hola Mundo
```

### CONLCUSIÓN

En esta práctica nos hemos familiarizado a usar Visul Studio Code, ya que sereá el entorno a usar en futuras prácticas, además hemos realizado nuestro primer código en TypeScript y JavaScript, dos lenguajes en cada práctica iremos adquiriendo un mayor conocimiento del mismo. Ta hemos terminado con las prácticas dedicadas a configurar el entorno de trabajo, las prácticas venideras estarán más enfocadas en la elaboración de ejercicios.

