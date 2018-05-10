---
title: 'Inicio rápido: usar Visual Studio para crear una aplicación web de Python'
description: En este inicio rápido, usará Visual Studio y el marco Flask para compilar una aplicación web simple en Python.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c21803f83baaac6a6a5d44764278d35e061d7d3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Inicio rápido: crear la primera aplicación web de Python con Visual Studio

En esta introducción a Visual Studio como un IDE de Python, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web Python basada en el marco Flask. El proyecto se crea mediante discretos pasos que le ayudarán a conocer las características básicas de Visual Studio.

Si todavía no ha instalado Visual Studio, vaya a la página [Descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalarlo de forma gratuita. En el instalador, asegúrese de seleccionar la carga de trabajo **Desarrollo de Python**.

## <a name="create-the-project"></a>Crear el proyecto

Los pasos siguientes crean un proyecto vacío que actúa como un contenedor para la aplicación:

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo > Nuevo > Proyecto**.

1. En el diálogo cuadro **Nuevo proyecto**, escriba "Proyecto web de Python" en el campo de búsqueda situado en la parte superior derecha, elija **Proyecto Web** en la lista del medio, asigne un nombre al proyecto (por ejemplo, "HelloPython") y luego elija **Aceptar**.

    ![Cuadro de diálogo Nuevo proyecto con Proyecto web de Python seleccionado](media/quickstart-python-00-web-project.png)

    Si no ve las plantillas de proyecto de Python, cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas > Obtener herramientas y características** para abrir el **instalador de Visual Studio**. Elija la carga de trabajo **Desarrollo de Python** y, luego, haga clic en **Modificar**.

    ![Carga de trabajo de desarrollo de Python en el instalador de Visual Studio](../python/media/installation-python-workload.png)

1. El nuevo proyecto se abre en el panel de la derecha del **Explorador de soluciones**. En este momento el proyecto está vacío porque no contiene ningún otro archivo.

    ![Explorador de soluciones con el proyecto vacío recién creado](media/quickstart-python-01-empty-project.png)

**Pregunta: ¿Cuál es la ventaja de crear un proyecto en Visual Studio para una aplicación de Python?**

**Respuesta**: Las aplicaciones de Python suelen definirse con el uso de carpetas y archivos únicamente, pero esta estructura sencilla puede ser más pesada a medida que las aplicaciones aumentan de tamaño y se generan posibles archivos de forma automática, JavaScript para aplicaciones web, etc. Un proyecto de Visual Studio le ayuda a administrar esta complejidad. El proyecto (un archivo *.pyproj*) identifica todos los archivos de origen y de contenido asociados al proyecto, contiene información de compilación para cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y le ayuda a organizar la aplicación en componentes lógicos.

**Pregunta: ¿Qué es la "solución" que se muestra en el Explorador de soluciones?**

**Respuesta**: Una solución de Visual Studio es un contenedor que le ayuda a administrar uno o más proyectos relacionados como un grupo y almacena los valores de configuración que no son específicos de un proyecto. Los proyectos de una solución también pueden hacerse referencia entre sí, de modo que la ejecución de un proyecto (una aplicación de Python) crea automáticamente un segundo proyecto (por ejemplo, una extensión de C++ usada en la aplicación de Python).

## <a name="install-the-flask-library"></a>Instalación de la biblioteca de Flask

En las aplicaciones web de Python casi siempre se usa una de las muchas bibliotecas de Python disponibles para controlar detalles de bajo nivel como el enrutamiento de solicitudes web y la forma de las respuestas. Para ello, Visual Studio proporciona una variedad de plantillas para aplicaciones web, una de las cuales se usará más adelante en este inicio rápido.

Aquí, utilice los pasos siguientes para instalar la biblioteca de Flask en el "entorno global" predeterminado que usa Visual Studio para este proyecto.

1. Expanda el nodo **Entornos de Python** en el proyecto para ver el entorno predeterminado para el proyecto.

    ![Explorador de soluciones en el que se muestra el entorno predeterminado](media/quickstart-python-02-default-environment.png)

1. Haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python**. Este comando abre la ventana **Entornos de Python** por la pestaña **Paquetes**.

1. Escriba "flask" en el campo de búsqueda y seleccione **instalación de PIP flask desde PyPI**. Acepte los mensajes de privilegios de administrador y observe el progreso en la ventana **Salida** de Visual Studio. (Se le pedirá confirmación de elevación cuando la carpeta de paquetes del entorno global esté ubicada en un área protegida, como *C:\Archivos de programa*).

    ![Instalación de la biblioteca de Flask](media/quickstart-python-03-install-package.png)

1. Una vez instalada, la biblioteca aparece en el entorno en el **Explorador de soluciones**, lo que significa que se puede usar en código de Python.

    ![Biblioteca de Flask instalada](media/quickstart-python-04-package-installed.png)

> [!Note]
> En lugar de instalar las bibliotecas en el entorno global, los desarrolladores suelen crear un "entorno virtual" en el que se instalan las bibliotecas de un proyecto específico. Las plantillas de Visual Studio normalmente ofrecen esta opción, como se describe en [Inicio rápido: Crear un proyecto de Python desde una plantilla en Visual Studio](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pregunta: ¿Dónde obtener más información acerca de los otros paquetes de Python disponibles?**

**Respuesta**: Visite el [índice de paquete de Python](https://pypi.org/).

## <a name="add-a-code-file"></a>Agregar un archivo de código

Ahora está listo para agregar un poco de código de Python para implementar una aplicación web básica.

1. Haga clic con el botón derecho en el **Explorador de soluciones** y seleccione **Agregar > Nuevo elemento**.

1. En el cuadro de diálogo que aparece, seleccione **Archivo de Python vacío**, asígnele el nombre *app.py* y seleccione **Agregar**. Visual Studio abre automáticamente el archivo en una ventana del editor.

1. Copie el siguiente código y péguelo en *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Puede haber observado que el cuadro de diálogo **Agregar > Nuevo elemento** muestra muchos otros tipos de archivos que puede agregar a un proyecto de Python, como una clase de Python, un paquete de Python, una prueba unitaria de Python, archivos *web.config*, etc. En general, estas plantillas de elemento, tal y como se denominan, son una excelente manera de crear rápidamente archivos con código reutilizable útil.

**Pregunta: ¿Dónde puedo obtener más información sobre Flask?**

**Respuesta**: Consulte la documentación de Flask, empezando por el [inicio rápido de Flask](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart).

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Haga clic con el botón derecho en *app.py* en el **Explorador de soluciones** y seleccione **Establecer como archivo de inicio**. Este comando identifica el archivo de código que se va a iniciar en Python cuando se ejecuta la aplicación.

    ![Establecimiento del archivo de inicio para un proyecto en el Explorador de soluciones](media/quickstart-python-05-set-as-startup-file.png)

1. Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades**. Después, haga clic en la pestaña **Depurar** y establezca la propiedad **Número de puerto** en `4449`. Este paso garantiza que Visual Studio inicia un explorador con `localhost:4449` para que coincida con los argumentos `app.run` en el código.

1. Seleccione **Depurar > Iniciar sin depurar** (**Ctrl**+**F5**) para guardar los cambios en los archivos y ejecutar la aplicación.

1. Aparece una ventana de comandos con el mensaje "* Ejecutando en https://localhost:4449/" y se abre una ventana del explorador para `localhost:4449` en la que se puede ver el mensaje "Hello, Python!". La solicitud GET también aparece en la ventana de comandos con un estado de 200.

    Si un explorador no se abre automáticamente, inicie el explorador que quiera y vaya a `localhost:4449`.

    Si solo ve el shell interactivo de Python en la ventana Comandos, o bien si esa ventana parpadea brevemente en la pantalla, asegúrese de haber establecido *app.py* como archivo de inicio anteriormente en el paso 1.

1. Vaya a `localhost:4449/hello` para comprobar que el elemento decorador para el recurso `/hello` también funciona. Una vez más, la solicitud GET aparece en la ventana de comandos con un estado de 200. No dude en probar algunas otras direcciones URL para ver que muestran los códigos de estado 404 en la ventana de comandos.

1. Cierre la ventana Comandos para detener la aplicación. Después, cierre la ventana del explorador.

**Pregunta: ¿Cuál es la diferencia entre el comando Iniciar sin depurar e Iniciar depuración?**

**Respuesta**: **Iniciar depuración** se usa para ejecutar la aplicación en el contexto del [depurador de Visual Studio](../python/debugging-python-in-visual-studio.md), lo que permite establecer puntos de interrupción, examinar las variables y recorrer el código línea por línea. Las aplicaciones se pueden ejecutar más lentamente en el depurador debido a los distintos enlaces que hacen posible la depuración. **Iniciar sin depurar**, en cambio, ejecuta la aplicación directamente como si la ejecutara desde la línea de comandos, sin contexto de depuración, y también inicia automáticamente un explorador y va a la dirección URL especificada en la pestaña **Depurar** de las propiedades del proyecto.

## <a name="next-steps"></a>Pasos siguientes

¡Enhorabuena por ejecutar su primera aplicación de Python desde Visual Studio, en la que ha aprendido un poco sobre el uso de Visual Studio como un IDE de Python!

Dado que los pasos realizados en este inicio rápido son bastante genéricos, probablemente se ha dado cuenta de que se pueden y deben automatizar. Tal automatización es el rol de las plantillas de proyecto de Visual Studio. Seleccione el botón siguiente para ver una demostración que crea una aplicación web similar a la que creó en este artículo, pero con menos pasos.

> [!div class="nextstepaction"]
> [Inicio rápido: Creación de un proyecto de Python con una plantilla](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

Para continuar con un tutorial más completo sobre Python en Visual Studio, incluido el uso de la ventana interactiva, depuración, visualización de datos y trabajar con Git, haga clic en el botón siguiente.

> [!div class="nextstepaction"]
> [Tutorial: Introducción a Python en Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Para explorar más de lo que Visual Studio ofrece, seleccione los siguientes vínculos.

- Más información sobre [plantillas de proyecto de aplicación web para Python](../python/python-web-application-project-templates.md)
- Más información sobre la [depuración de Python](../python/debugging-python-in-visual-studio.md)
- Más información sobre el [IDE de Visual Studio](../ide/visual-studio-ide.md) en general
