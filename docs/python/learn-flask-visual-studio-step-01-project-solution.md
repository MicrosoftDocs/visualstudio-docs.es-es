---
title: 'Tutorial: Información sobre Flask en Visual Studio, paso 1'
description: Tutorial sobre aspectos básicos de Flask en el contexto de los proyectos de Visual Studio.
ms.date: 06/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: f64c603d9902343d83b57d56ab891c7b41d021ae
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586409"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Tutorial: Introducción al marco web de Flask en Visual Studio

[Flask](http://flask.pocoo.org/) es un marco de Python ligero para aplicaciones web que proporciona los elementos básicos para el enrutamiento de direcciones URL y la representación de páginas.

Flask es un "micromarco" porque no proporciona de forma directa características como la validación de formularios, la abstracción de bases de datos, la autenticación, etc. Dichas características se proporcionan en paquetes especiales de Python llamados *extensiones* de Flask. Las extensiones se integran perfectamente con Flask para que aparezcan como si formaran parte del mismo Flask. Por ejemplo, Flask por sí solo no proporciona un motor de plantillas de página. La creación de plantillas se proporciona mediante extensiones como Jinja y Jade, como se muestra en este tutorial.

En este tutorial aprenderá a:

> [!div class="checklist"]
> - Crear un proyecto básico de Flask en un repositorio de Git con la plantilla "Proyecto web de Flask en blanco" (paso 1)
> - Crear una aplicación de Flask con una página y representar esa página con una plantilla (paso 2)
> - Atender archivos estáticos, agregar páginas y usar la herencia de plantilla (paso 3)
> - Usar la plantilla Proyecto web de Flask para crear una aplicación con varias páginas y diseño con capacidad de respuesta (paso 4)
> - Use la plantilla Proyecto web de Flask de sondeos para crear una aplicación de sondeos que use una serie de opciones de almacenamiento (Azure Storage, MongoDB o memoria).

En el transcurso de estos pasos creará una única solución de Visual Studio que contendrá tres proyectos independientes. Creará el proyecto mediante distintas plantillas de proyecto de Flask que se incluyen con Visual Studio. Al mantener los proyectos en la misma solución, puede cambiar fácilmente entre distintos archivos para compararlos.

> [!Note]
> Este tutorial difiere del [inicio rápido de Flask](../ide/quickstart-python.md?context=visualstudio/python/default) en el sentido de que obtendrá más información sobre Flask y sobre cómo usar las distintas plantillas de proyecto de Flask que proporcionan un punto de partida más amplio para sus propios proyectos. Por ejemplo, las plantillas de proyecto instalan automáticamente el paquete de Flask al crear un proyecto, en lugar de tener que instalarlo manualmente, como se muestra en el inicio rápido.

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio 2017 en Windows con las siguientes opciones:
  - La carga de trabajo **Desarrollo de Python** (pestaña **Carga de trabajo** del instalador). Para obtener instrucciones, vea [Instalación de la compatibilidad con Python en Visual Studio en Windows](installing-python-support-in-visual-studio.md).
  - **Git para Windows** y **Extensión de GitHub para Visual Studio** en la pestaña **Componentes individuales** de **Herramientas de código**.

Las plantillas de proyecto de Flask se incluyen con todas las versiones anteriores de las Herramientas de Python para Visual Studio, aunque los detalles pueden diferir de lo que se describe en este tutorial.

El desarrollo de Python no es compatible actualmente en Visual Studio para Mac. En Mac y Linux, use la [extensión de Python en Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Paso 1.1: Crear una solución y un proyecto de Visual Studio

1. En Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto**, busque "Flask" y seleccione la plantilla **Proyecto web de Flask en blanco**. (La plantilla también se encuentra en **Python** > **Web** en la lista de la izquierda).

    ![Cuadro de diálogo Nuevo proyecto en Visual Studio para el Proyecto web de Flask en blanco](media/flask/step01-new-blank-project.png)

1. En los campos de la parte inferior del cuadro de diálogo, escriba la información siguiente (como se muestra en el gráfico anterior) y, a continuación, seleccione **Aceptar**:

    - **Nombre**: establezca el nombre del proyecto de Visual Studio en **BasicProject**. Este nombre también se usa para el proyecto de Flask.
    - **Ubicación**: especifique una ubicación en la que se va a crear la solución y el proyecto de Visual Studio.
    - **Nombre de la solución**: establezca en **LearningFlask**, que es adecuado para la solución como contenedor de varios proyectos de este tutorial.
    - **Crear directorio para la solución**: deje el valor predeterminado.
    - **Crear nuevo repositorio Git**: active esta opción (que está desactivada de forma predeterminada) para que Visual Studio cree un repositorio Git local al generar la solución. Si no ve esta opción, ejecute el instalador de Visual Studio 2017 y agregue **Git para Windows** y la **Extensión de GitHub para Visual Studio** en la pestaña **Componentes individuales**, en **Herramientas de código**.

1. Tras un momento, Visual Studio muestra un cuadro de diálogo que indica **Este proyecto necesita paquetes externos** (se muestra abajo). Este cuadro de diálogo aparece porque la plantilla incluye un archivo *requirements.txt* que hace referencia al paquete Flask 1.x más reciente. (Active **Mostrar paquetes necesarios** para ver las dependencias exactas).

    ![Cuadro de diálogo que indica que el proyecto requiere paquetes externos](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Seleccione la opción **Los instalaré de forma manual**. Cree el entorno virtual en breve para asegurarse de que se excluye del control de código fuente. (El entorno siempre puede crearse a partir de *requirements.txt*).

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Paso 1.2: Examinar los controles de Git y publicar en un repositorio remoto

Como seleccionó **Crear nuevo repositorio Git** en el cuadro de diálogo **Nuevo proyecto**, el proyecto ya estará confirmado para el control de código fuente local en cuanto se complete el proceso de creación. En este paso, familiarícese con los controles de Git de Visual Studio y la ventana de **Team Explorer** en la que se trabaja con el control de código fuente.

1. Examine los controles de Git en la esquina inferior de la ventana principal de Visual Studio. De izquierda a derecha, estos controles muestran confirmaciones sin insertar, cambios sin confirmar, el nombre del repositorio y la rama actual:

    ![Controles de Git en la ventana de Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Si no selecciona **Crear nuevo repositorio Git** en el cuadro de diálogo **Nuevo proyecto**, los controles de Git solo muestran un comando **Agregar al control de código fuente** que crea un repositorio local.
    >
    > ![Agregar al control de código fuente aparece en Visual Studio si no ha creado un repositorio](media/tutorials-common/step01-git-add-to-source-control.png)

1. Seleccione el botón de cambios y Visual Studio abre su ventana de **Team Explorer** en la página **Cambios**. Dado que el proyecto recién creado ya se ha confirmado automáticamente en el control de código fuente, no verá cambios pendientes.

    ![Ventana de Team Explorer en la página Cambios](media/flask/step01-team-explorer-changes.png)

1. En la barra de estado de Visual Studio, haga clic en el botón de confirmaciones sin insertar (la flecha arriba con **2**) para abrir la página **Sincronización** en **Team Explorer**. Como tiene solo un repositorio local, la página ofrece opciones sencillas para publicar el repositorio en repositorios remotos diferentes.

    ![Ventana de Team Explorer que muestra las opciones de repositorio Git para el control de código fuente](media/flask/step01-team-explorer.png)

    Puede elegir cualquier servicio que desee para sus propios proyectos. En este tutorial se muestra el uso de GitHub, donde se mantiene el código de ejemplo completo del tutorial en el repositorio [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

1. Al seleccionar cualquiera de los controles de **Publicar**, **Team Explorer** le pedirá más información. Por ejemplo, al publicar el ejemplo para este tutorial, el propio repositorio tenía que haberse creado primero. En este caso, la opción **Insertar en repositorio remoto** se utilizó con la dirección URL del repositorio.

    ![Ventana de Team Explorer para insertar en un repositorio remoto existente](media/flask/step01-push-to-github.png)

    Si no tiene ningún repositorio, las opciones **Publish to GitHub** (Publicar en GitHub) e **Insertar en Visual Studio Team Services** le permiten crear uno directamente desde Visual Studio.

1. Mientras esté trabajando en este tutorial, adopte la costumbre de usar los controles de Visual Studio periódicamente para confirmar e insertar los cambios. Este tutorial se lo recuerda en los momentos adecuados.

> [!Tip]
> Para desplazarse rápidamente por **Team Explorer**, seleccione el encabezado (donde pone **Changes** o **Push** en las imágenes anteriores) para ver un menú emergente de las páginas disponibles.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pregunta: ¿Cuáles son algunas de las ventajas del uso de control de código fuente desde el principio de un proyecto?

Respuesta: En primer lugar, usar el control de código fuente desde el principio, especialmente si también utiliza un repositorio remoto, genera una copia de seguridad periódica externa del proyecto. A diferencia de mantener un proyecto solo en un sistema de archivos local, el control de código fuente también proporciona un historial de cambios completo y la capacidad de revertir con facilidad un único archivo o todo el proyecto a un estado anterior. Ese historial de cambios ayuda a determinar la causa de regresiones (errores de prueba). Además, el control de código fuente es esencial si varias personas trabajan en un proyecto, ya que administra las sobrescrituras y ofrece solución para los conflictos. Por último, el control de código fuente, que es básicamente una forma de automatización, facilita la automatización de las compilaciones, las pruebas y la administración de versiones. Es realmente el primer paso para utilizar DevOps para un proyecto, y dado que las barreras de entrada son tan bajas, realmente no hay ninguna razón que impida usar el control de código fuente desde el principio.

Para obtener más información sobre el control de código fuente como automatización, consulte [The Source of Truth: The Role of Repositories in DevOps](https://msdn.microsoft.com/magazine/mt763232) (El origen de la verdad, el rol de los repositorios en DevOps), un artículo de MSDN Magazine escrito para aplicaciones móviles que se aplica también a las aplicaciones web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pregunta: ¿Puedo evitar que Visual Studio confirme automáticamente un nuevo proyecto?

Respuesta : Sí. Para deshabilitar la confirmación automática, vaya a la página **Configuración** de **Team Explorer**, seleccione **Git** > **Configuración global**, desactive la opción **Confirmar cambios tras la fusión mediante combinación de forma predeterminada** y, a continuación, seleccione **Actualizar**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Paso 1.3: Crear el entorno virtual y excluirlo del control de código fuente

Ahora que ha configurado el control de código fuente para el proyecto, puede crear el entorno virtual para los paquetes Flask necesarios que requiere el proyecto. A continuación, puede usar **Team Explorer** para excluir la carpeta del entorno del control de código fuente.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual**.

    ![Comando Agregar entorno virtual en el Explorador de soluciones](media/flask/step01-add-virtual-environment-command.png)

1. Aparece un cuadro de diálogo **Agregar entorno virtual** con un mensaje que indica **Hemos encontrado un archivo requirements.txt**. Este mensaje indica que Visual Studio usa ese archivo para configurar el entorno virtual.

    ![Cuadro de diálogo Agregar entorno virtual con mensaje requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Seleccione **Crear** para aceptar los valores predeterminados. (Puede cambiar el nombre del entorno virtual si lo desea, lo cual simplemente cambia el nombre de su subcarpeta, pero `env` es una convención estándar).

1. Dé su consentimiento para los privilegios de administrador si se le solicita y tenga paciencia durante unos minutos mientras Visual Studio descarga e instala los paquetes, lo que para Flask y sus dependencias implica expandir cerca de miles de archivos en más de 100 subcarpetas. Puede ver el progreso en la ventana **Salida** de Visual Studio. Mientras espera, consulte la sección Preguntas a continuación. También puede ver una descripción de las dependencias de Flask en la página de [instalación de Flask](http://flask.pocoo.org/docs/1.0/installation/#installation) (flask.pcocoo.org).

1. En los controles de Git de Visual Studio (en la barra de estado), seleccione el indicador de cambios (que muestra **99&#42;**) que abre la página **Cambios** en **Team Explorer**.

    La creación del entorno virtual implica cientos de cambios, pero no es necesario que incluya ninguno de ellos en el control de código fuente, dado que usted (o cualquier usuario que clone el proyecto) siempre puede volver a crear el entorno a partir de *requirements.txt*.

    Para excluir el entorno virtual, haga clic con el botón derecho en la carpeta **env** y seleccione **Omitir estos elementos locales**.

    ![Omisión de un entorno virtual en los cambios de control de código fuente](media/flask/step01-ignore-local-items.png)

1. Después de excluir el entorno virtual, los únicos cambios que faltan son en el archivo de proyecto y en *.gitignore*. El archivo *.gitignore* contiene una entrada agregada para la carpeta del entorno virtual. Puede hacer doble clic en el archivo para ver las diferencias.

1. Escriba un mensaje de confirmación y seleccione el botón **Confirmar todo**, a continuación, inserte las confirmaciones en el repositorio remoto si lo desea.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pregunta: ¿Por qué es conveniente crear un entorno virtual?

Respuesta: Un entorno virtual es una excelente manera de aislar las dependencias exactas de la aplicación. Este tipo de aislamiento evita conflictos dentro de un entorno de Python global y contribuye a las pruebas y la colaboración. Con el tiempo, a medida que desarrolle una aplicación, es inevitable que incorpore muchos paquetes útiles de Python. Si mantiene los paquetes en un entorno virtual específico del proyecto, puede actualizar fácilmente el archivo *requirements.txt* del proyecto que describe ese entorno, el cual se incluye en el control de código fuente. Cuando el proyecto se copia en otros equipos, como los servidores de compilación, los servidores de implementación y otros equipos de desarrollo, es fácil volver a crear el entorno con solo *requirements.txt* (por este motivo no es necesario que el entorno esté en el control de código fuente). Para obtener más información, vea [Use virtual environments](selecting-a-python-environment-for-a-project.md#use-virtual-environments) (Usar entornos virtuales).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pregunta: ¿Cómo se quita un entorno virtual que ya se ha confirmado en el control de código fuente?

Respuesta: En primer lugar, edite el archivo *.gitignore* para excluir la carpeta: busque la sección del final con el comentario `# Python Tools for Visual Studio (PTVS)` y agregue una línea nueva para la carpeta del entorno virtual, como `/BasicProject/env`. (Dado que Visual Studio no muestra el archivo en el **Explorador de soluciones**, ábralo directamente mediante el comando de menú **Archivo** > **Abrir** > **Archivo**. También puede abrir el archivo desde **Team Explorer**: en la página **Configuración**, seleccione **Configuración de repositorios**, vaya a la sección **Archivos de omisión y de atributos** y luego seleccione el vínculo **Editar** junto a **.gitignore**).

En segundo lugar, abra una ventana de comandos, vaya a la carpeta como *BasicProject* que contiene la carpeta del entorno virtual, como *env*, y ejecute `git rm -r env`. A continuación, confirme esos cambios desde la línea de comandos (`git commit -m 'Remove venv'`), o bien desde la página **Cambios** de **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Paso 1.4: Examinar el código reutilizable

1. Cuando termina la creación del proyecto, se ven la solución y el proyecto en el **Explorador de soluciones**, donde el proyecto contiene solo dos archivos, *app.py* y *requirements.txt*:

    ![Archivos de proyecto de Flask en blanco en el Explorador de soluciones](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Como se ha indicado antes, el archivo *requirements.txt* especifica la dependencia del paquete de Flask. La presencia de este archivo es lo que le invita a crear un entorno virtual cuando empiece a crear el proyecto.

1. El archivo *app.py* único consta de tres partes. La primera es una instrucción `import` para Flask, en la que se crea una instancia de la clase `Flask`, que se asigna a la variable `app`, y luego se asigna una variable `wsgi_app` (que es útil cuando se implementa en un host web, pero no se usa en este momento):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. La segunda parte, al final del archivo, es un fragmento de código opcional que inicia el servidor de desarrollo de Flask con unos valores de host y de puerto específicos que se han tomado de las variables de entorno (el valor predeterminado es localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. La tercera es un fragmento de código que asigna una función a una ruta de dirección URL, lo que significa que la función proporciona el recurso identificado por la dirección URL. Las rutas se definen con el decorador `@app.route` de Flask, cuyo argumento es la dirección URL relativa de la raíz del sitio. Como puede ver en el código, aquí la función solo devuelve una cadena de texto, que basta para representar un explorador. En los pasos siguientes se representan páginas más enriquecidas con HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-name-argument-to-the-flask-class"></a>Pregunta: ¿Cuál es el propósito del argumento __name__ para la clase de Flask?

Respuesta: El argumento es el nombre del módulo o del paquete de la aplicación e indica a Flask dónde se deben buscar plantillas, archivos estáticos y otros recursos que pertenecen a la aplicación. Para las aplicaciones incluidas en un solo módulo, `__name__` siempre es el valor adecuado. También es importante para las extensiones que necesitan información de depuración. Para obtener más información y argumentos adicionales, vea la [documentación sobre las clases de Flask](http://flask.pocoo.org/docs/1.0/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pregunta: ¿Una función puede tener más de un decorador de ruta?

Respuesta: Sí, puede usar todos los decoradores que quiera si la misma función sirve para varias rutas. Por ejemplo, para usar la función `hello` para "/" y "/hello", use el código siguiente:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pregunta: ¿Cómo trabaja Flask con las rutas de dirección URL de variables y con los parámetros de consulta?

Respuesta: En una ruta, las variables se marcan con `<variable_name>` y Flask pasa la variable a la función con un argumento con nombre. La variable puede formar parte de la ruta de acceso de la dirección URL o de un parámetro de consulta. Por ejemplo, una ruta con el formato `'/hello/<name>` genera un argumento de cadena denominado `name` en la función. Al usar `?message=<msg>` en la ruta, se analiza el valor indicado para el parámetro de consulta "message=" y se pasa a la función como `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Para cambiar el tipo, anteponga la variable con `int`, `float`, `path` (que acepta barras diagonales para delinear los nombres de las carpetas) y `uuid`. Para obtener información detallada, vea las [reglas de las variables](http://flask.pocoo.org/docs/1.0/quickstart/#variable-rules) en la documentación de Flask.

Los parámetros de consulta también están disponibles mediante la propiedad `request.args`, en concreto mediante el método `request.args.get`. Para obtener más información, vea la información sobre el [objeto Request](http://flask.pocoo.org/docs/1.0/quickstart/#the-request-object) de la documentación de Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pregunta: ¿Puede Visual Studio generar un archivo requirements.txt a partir de un entorno virtual después de instalar otros paquetes?

Respuesta : Sí. Expanda el nodo **Entornos de Python**, haga clic con el botón derecho en su entorno virtual y seleccione el comando **Generar requirements.txt**. Es conveniente usar este comando periódicamente a medida que modifica el entorno, y confirmar los cambios de *requirements.txt* en el control de código fuente junto con cualquier otro cambio de código que dependa de ese entorno. Si configura la integración continua en un servidor de compilación, debe generar el archivo y confirmar los cambios cada vez que se modifique el entorno.

## <a name="step-1-5-run-the-project"></a>Paso 1-5: ejecutar el proyecto

1. En Visual Studio, seleccione **Depurar** > **Iniciar depuración** (**F5**) o use el botón **Servidor web** de la barra de herramientas (el explorador puede variar):

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Cualquiera de los comandos asigna un número de puerto aleatorio a la variable de entorno PORT y, luego, ejecuta `python app.py`. El código inicia la aplicación usando ese puerto en el servidor de desarrollo de Flask. Si Visual Studio indica **No se pudo iniciar el depurador** con un mensaje relacionado con la falta de un archivo de inicio, haga clic con el botón derecho en **app.py** en el **Explorador de soluciones** y seleccione **Establecer como archivo de inicio**.

1. Al iniciar el servidor, verá una ventana de consola abierta en la que se muestra el registro del servidor. Luego, Visual Studio abre automáticamente un explorador en `http://localhost:<port>`, donde debería ver el mensaje que se representa mediante la función `hello`:

    ![Vista predeterminada del proyecto de Flask](media/flask/step01-first-run-success.png)

1. Cuando haya terminado, detenga el servidor cerrando la ventana de la consola o con el comando **Depurar** > **Detener depuración** en Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pregunta: ¿Cuál es la diferencia entre el uso de los comandos de menú de depuración y los comandos de servidor en el submenú de Python del proyecto?

Respuesta: Además de con los comandos de menú de **Depurar** y los botones de la barra de herramientas, también puede iniciar el servidor mediante los comandos **Python** > **Run server** (Ejecutar servidor) o **Python** > **Run debug server** (Iniciar el servidor de depuración) en el menú contextual del proyecto. Ambos comandos abren una ventana de consola en la que se ve la dirección URL local (localhost:port) del servidor en ejecución. Sin embargo, debe abrir manualmente un explorador con esa dirección URL, y la ejecución del servidor de depuración no inicia automáticamente el depurador de Visual Studio. Puede adjuntar un depurador al proceso en ejecución más adelante, si lo desea, mediante el comando **Depurar** > **Asociar al proceso**.

## <a name="next-steps"></a>Pasos siguientes

En este momento, el proyecto básico de Flask contiene el código de inicio y el código de página en el mismo archivo. Es mejor separar estos dos elementos y separar también el código HTML y los datos mediante plantillas.

> [!div class="nextstepaction"]
> [Creación de una aplicación de Flask con vistas y plantillas de página](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Inicio rápido de Flask](http://flask.pocoo.org/docs/1.0/quickstart/) (flask.pocoo.org)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
