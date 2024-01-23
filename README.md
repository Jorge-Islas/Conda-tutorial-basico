# Tutorial básico de conda

## Qué es conda

`conda` es una herramienta que permite crear *entornos virtuales* de python (aunque también soporta otros lenguajes como R y proyectos multilenguaje), en los cuales se pueden listar, instalar y desinstalar paquetes dentro de cada uno de estos entornos. Esto te permite poder instalar diferentes versiones de paquetes para distintos proyectos que tengas sin causar problemas de compatibilidad entre ellos.

Para utilizar `conda` como tu gestor de paquetes de python puedes descargarlo e instalarlo en dos versiones: **Anaconda** o **Miniconda**. La diferencia principal entre estas dos presentaciones es que Miniconda incluye los paquetes mínimos indispensables para poder utilizar `conda`, mientras que Anaconda incluye más herramientas y funcionalidades pero es más pesado. Si quieres saber cuales son las diferencias, pros y contras de estas presentaciones da clic aquí:
[Diferencias entre Anaconda y Miniconda.](https://jorgeislas.com/)

### Instrucciones de instalación de Anaconda y Miniconda

Tanto **Anaconda** como **Miniconda** pueden instalarse en Windows, MacOS y Linux. Dando clic a estos enlaces puedes ver las instrucciones de instalación de **Anaconda** y **Miniconda**, respectivamente: 

[![Static Badge](https://img.shields.io/badge/-Instalaci%C3%B3n%20Anaconda-%23000000?logo=anaconda&logoColor=%23fbfbfb&labelColor=%2344A833&color=%230c0c0c)](https://docs.anaconda.com/free/anaconda/install/) 
[![Static Badge](https://img.shields.io/badge/-Instalaci%C3%B3n%20Miniconda-%23000000?logo=anaconda&logoColor=%23fbfbfb&labelColor=%2344A833&color=%230c0c0c)](https://docs.conda.io/projects/miniconda/en/latest/)

## Primeros pasos

Para poder utilizar los siguientes comandos es necesario ya haber instalado e inicializado **Anaconda** o **Miniconda**. 

Si usas **Windows** deberás abrir el programa llamado:

- *Anaconda Prompt (anaconda3)*
- *Anaconda Prompt (miniconda3)*

o si usas la versión de Powershell:

- *Anaconda Powershell Prompt (anaconda3)*
- *Anaconda Powershell Prompt (miniconda3)*.

Si usas MacOS o Linux deberás abrir una terminal y verificar que hayas inicializado `conda` como se indica en las instrucciones de instalación.

### Verificar instalación de conda

Para verificar si `conda` se ha instalado correctamente, usa este comando para revisar la versión de `conda` que has instalado:

```
conda --version
```

Si al ingresar este comando y dar enter te apareció algo como esto: `conda 23.11.0`, entonces `conda` se ha instalado correctamente. En caso contrario, algo ha ido mal con la instalación o la inicialización de `conda`.

### Crear entorno virtual de conda

Antes de instalar algún paquete es muy importante crear un *entorno virtual*, el cual es como una caja en la cual vas a poner todos los paquetes que vayas a utilizar en tu proyecto, aislándolos de otras cajas que corresponden a otros de tus proyectos. Esto te permitirá evitar problemas de compatibilidad de versiones entre tus paquetes e incluso versiones python en tus proyectos.

Ingresa el siguiente comando reemplazando `NOMBRE` por el nombre que le quieras dar a tu entorno:

```
conda create -n NOMBRE
```

Una vez que des enter, sigue las instrucciones de creación de entorno que te aparezcan el la terminal o consola de comandos.

### Activar entorno de conda

Después de terminar de crear tu entorno virtual y antes de hacer cualquier otra acción (como instalar algún paquete o inicializar alguna herramienta), deberás activar tu entorno utilizando el siguiente comando reemplazando `NOMBRE` con el nombre que le hayas dado a tu entorno:

```
conda activate NOMBRE
```

### Instalar un paquete dentro del entorno

Una vez activado tu entorno, prueba a instalar el paquete **numpy**, el cual permite utilizar operaciones con vectores y matrices, con el siguiente comando:

```
conda install numpy
```

Después de dar enter sigue las instrucciones de instalación del paquete. Es posible que al instalar paquetes `conda` te indique que es necesario instalar otros paquetes, estos se conocen como *dependencias* del paquete que quieres instalar, esto significa que dicho paquete necesita todos esos paquetes adicionales para poder funcionar.

### Revisar paquetes instalados en el entorno

Para poder revisar qué paquetes se han instalado en tu entorno activo de `conda` puedes utilizar el siguiente comando:

```
conda list
```

## Comandos esenciales

<details>
<summary><strong>Da clic para expandir</strong></summary>
<br>

**Información, versión y actualizar conda**

- `conda --version` : Indica la versión de `conda` instalada.

- `conda info` : Muestra toda la información de la instalación de `conda`.

- `conda update conda` : Actualiza `conda` a su versión más reciente en el entorno actual.

**Obtener ayuda de comandos de conda**

- `conda NOMBRE_COMANDO --help` : Muestra la ayuda y documentación del comando indicado.

**Crear, renombrar y clonar entornos de conda**

- `conda info --envs` : Muestra la lista de todos los entornos de `conda` existentes. También se puede utilizar el comando `conda env list`.

- `conda create --name NOMBRE` : Crea un entorno de `conda`. Reemplaza `NOMBRE` por el nombre que le quieras dar al entorno.

- `conda create -n NOMBRE python=VERSION` : Crea un entorno de `conda` utilizando la versión de python especificada en `VERSION` (por ejemplo, 3.9). Reemplaza `NOMBRE` por el nombre que le quieras dar al entorno.

- `conda create -n NOMBRE -f environment.yml` : Crea un entorno de `conda` a partir de las especificaciones dadas en el archivo `environment.yml`. Reemplaza `NOMBRE` por el nombre que le quieras dar al entorno.

- `conda rename -n NOMBRE NUEVO_NOMBRE` : Cambia el nombre del entorno `NOMBRE` al nuevo nombre `NUEVO_NOMBRE`.

- `conda create --name NOMBRE_CLON --clone NOMBRE` : Crea una copia del entorno llamado `NOMBRE` y le asingna el nombre `NOMBRE_CLON` al entorno copia creado.

**Activar y desactivar entornos de conda**

- `conda activate NOMBRE` : Activa el entorno de conda llamado `NOMBRE`.

- `conda deactivate` : Desactiva el entorno actualmente en uso y activa el entrono `base`.

**Revisar paquetes instalados en entornos de conda**

`conda list`

`conda list -n myenv`

`conda list -n myenv NOMBRE_PAQUETE`

**Eliminar entornos de conda**

`conda remove -n NOMBRE --all`

**Instalar y desinstalar paquetes en entornos de conda**

`conda install NOMBRE_PAQUETE`

`conda install NOMBRE_PAQUETE=NUMERO_VERSION`

`conda install -c NOMBRE_CANAL NOMBRE_PAQUETE`

`conda uninstall NOMBRE_PAQUETE`

**Exportar entornos de conda**

`conda env export > environment.yml`

`conda env export --from-history > environment.yml`

**Importar entornos de conda**

`conda create -n NOMBRE --file ARCHIVO.yml`

`conda create -n NOMBRE --file ARCHIVO.txt`

</details>