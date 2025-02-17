#  Jupyter Notebooks

En este repositorio tenemos un archivo `docker-compose.yml` configurado para poder lanzar una instancia local de Jupyter Notebook.

Se ha mapeado el directorio local `notebooks` al directorio de trabajo `/home/jovyan/work`, por lo que sólo deberemos copiar los archivos `.ipynb` en dicho directorio y nos aparecerá directamente en la interfaz de usuario.

## Inicio

Podemos clonar el directorio en nuestra máquina:

```bash
git clone https://github.com/jmfdiazAL/jupyter-notebook.git
```

Nos vamos al directorio raíz:

```bash
cd jupyter-notebook
```

Iniciamos el servidor de Jupyter Notebook:

```bash
docker compose up
```

Tras descargarse la imagen, podremos acceder en la dirección http://localhost:8888.

## Uso en GitHub Codespaces

Este repositorio se ha probado en GitHub Codespaces de dos maneras.

 - Ejecutando el archivo `docker-compose.yml` en el entorno creado por Codespaces.
 - Desde el propio Github, y pulsando en las opciones del entorno creado, elegiremos la opción *Open in JupyterLab*, aunque es una opción *Preview*.

## Estructura de directorios
  
-  `./notebooks`: Este directorio es dónde podemos añadir nuestros cuadernos de Jupyter. Como se dijo en la introducción, se ha montado como un volumen mapeado, por lo que los cuadernos creados y guardados en *Jupyter Notebook IDE* se almacenarán ahí..

> [!TIP]
> Los ejemplos sumnistrados en este repositorio se han creado desde las plantillas de [DataLab](https://www.datacamp.com/datalab), donde podemos encontrar más ejemplos de donde partir.

## Notas

Al lanzar el contenedor, se ejecuta el comando `start-notebook.sh`con el parámetro `--NotebookApp.token=`, lo que hace que no se nos pida ningún token al entrar al servidor.

Si queremos modificar el directorio por defecto al arrancar podríamos modificar la opción `--ServerApp.root_dir=/home/jovyan/work`. (en este caso coincide con el directorio mapeado)

Si queremos abrir directamente JupyterLab desde GitHub es mejor usar el repositorio https://github.com/jmfdiazAL/codespaces-jupyter, generado a parttir de las plantillas de GitHub, y que no tiene ningún archivo de Docker aunque se pueden personalizar los paquetes necesarios editando el archivo `requirements.txt`.

Se ha usado por simplicidad la imagen mas reciente de [quay.io/jupyter/datascience-notebook][1] que ya trae la mayoría de los paquetes necesarios para el tratamiento de datos, incluidos R y Julia. Si queremos personalizar la imagen podemos crear una imagen personalizada añadiendo las dependencias en el archivo `requirements.txt` tal y como se hace en el repositorio https://github.com/nezhar/jupyter-docker-compose.

[1]: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-datascience-notebook