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



















## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct02-vscode-Espinette/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct02-vscode-Espinette/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
