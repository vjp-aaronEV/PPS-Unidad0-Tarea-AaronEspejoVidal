# Proceso de creación del Workflow para crear la estructura de MkDocs

## CreacionDocumentacion.yml
El archivo **.yml** que hagamos tiene que estar en la carpeta `.github/workflows/`, en este caso el archivo se llama: **CreacionDocumentacion.yml**, estos son los pasos que yo he seguido para crear este fichero:

- Lo primero que tenemos que poner en este archivo es el nombre que le queremos dar al flujo de trabajo con la etiqueta `name:`.
- Luego tenemos que utilizar la etiqueta `on:`, dentro de esta tenemos que especificar los eventos que tienen que suceder para que se ejecute el flujo de trabajo:
    - `push:`: Cada vez que se haga un push se ejcuta
    - `branches:`: Especifica las ramas donde se tiene que realizar el evento para que se ejecute
    - `- main`: En este caso únicamente sucede cuando se hace un push en la rama main
- Dentro del bloque de la etiqueta `permissions:` tenemos que especificar los permisos que va a tener el flujo de trabajo:
    - `contents`: Permite leer y escribir los archivos del repositorio
    - `pages`: Permite configurar y publicar en Github Pages.
    - `id-token`: Permite solicitar tokens de OpenID Connect 
- Dentro del bloque de la etiqueta `jobs:` tenemos que especificar los trabajos que queremos que haga el flujo
    - `deploy:`: Es el nombre que le damos al flujo, puede llamarse de cualquier manera. En este caso solamente tiene un trabajo
        - `runs-on: ubuntu-latest`: Especifica que todas los pasos se tienen que ejecutar en el contenedor de ubuntu-latest
    - `steps:`: Los pasos que se tienen ejecutar en el flujo. En este caso son estos:
        - Clonar el repositorio al entorno de trabajo del Runner  
        - Configurar el entorno de Python que va a utilizar MkDocs
        - Instalación de las dependencias necesarias para MkDocs e instalar MkDocs con el comando dentro del contenedor de ubuntu: `pip install mkdocs`
        - Construcción y despliegue de la documentación
### Captura de pantalla del documento CreacionDocumentacion.yml
![Captura de pantalla creacionDocumentacion.yml](imagenes/5CreacionWorkflow.png)

---

## Creación mkdocs.md 
- Primero de todo tenemos que utilizar la etiqueta `site name:` para especificar el título de la pestaña y de la página.
- Dentro del bloque de la etiqueta `nav` ponemos la lista de los enlaces a los archivos de la documentación para que mkdocs sepa cuales son.
- En la etiqueta `doc_dirs:` tenemos que especificar la carpeta donde están los archivos de documentación del proyecto.

### Captura de pantalla del documento mkdocs.md
![Captura de pantalla mkdocs.md](imagenes/6CreacionMkDocs.png)

## Push de la creación del Workflow y comprobación de funcionamiento
En estas dos capturas de pantalla se va a poder ver como hago el push a github y en la pestaña de **'Actions'** de la página web de Github se ha ejecutado el Workflow correctamente
![Captura de pantalla push a github](imagenes/7PushWorkflow.png)
![Captura de pantalla comprobación del workflow](imagenes/8ComprobacionWorkflow.png)
