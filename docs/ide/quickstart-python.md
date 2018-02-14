---
title: "Inicio rápido: usar Visual Studio para crear su primera aplicación web Python | Microsoft Docs"
description: "Una breve introducción al uso de Python en Visual Studio que crea una aplicación web sencilla con el marco de trabajo de Falcon."
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
dev_langs:
- python
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 00b9d59ad1736d212dcd9fff3c097e81e0ad2a60
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Inicio rápido: usar Visual Studio para crear su primera aplicación web Python

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web Python. Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

## <a name="create-the-project"></a>Crear el proyecto

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo > Nuevo > Proyecto...**.

1. En el cuadro de diálogo **Nuevo proyecto**, en el panel de la izquierda, expanda **Instalado** y, después, seleccione **Python**.

1. En el panel central, elija **Proyecto web**, asigne al proyecto un nombre como "HelloPython" y luego haga clic en **Aceptar**.

    ![Cuadro de diálogo Nuevo proyecto con Proyecto web de Python seleccionado](media/quickstart-python-00-web-project.png)

    Si no ve las plantillas de proyecto de Python, cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas > Obtener herramientas y características...** para abrir el instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Python** y, luego, haga clic en **Modificar**.

    ![Carga de trabajo de desarrollo de Python en el instalador de Visual Studio](../python/media/installation-python-workload.png)

1. El nuevo proyecto se abre en el panel de la derecha del **Explorador de soluciones**. En este momento el proyecto está vacío porque no contiene ningún otro archivo.

    ![Explorador de soluciones con el proyecto vacío recién creado](media/quickstart-python-01-empty-project.png)

**Pregunta: ¿Cuál es la ventaja de crear un proyecto en Visual Studio para una aplicación de Python?**

Respuesta: Las aplicaciones de Python suelen definirse con el uso de carpetas y archivos únicamente, pero esta estructura puede ser más compleja a medida que las aplicaciones aumentan de tamaño y se generan posibles archivos de forma automática, JavaScript para aplicaciones web, etc. Un proyecto de Visual Studio le ayuda a administrar esta complejidad. El proyecto (un archivo `.pyproj`) identifica todos los archivos de origen y de contenido asociados al proyecto, contiene información de compilación para cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y le ayuda a organizar la aplicación en componentes lógicos.

## <a name="install-the-falcon-library"></a>Instalar la biblioteca Falcon

En las aplicaciones web de Python casi siempre se usa una de las muchas bibliotecas de Python disponibles para controlar detalles de bajo nivel como el enrutamiento de solicitudes web y la forma de las respuestas. Para ello, Visual Studio proporciona una variedad de plantillas para aplicaciones web mediante los marcos Bottle, Flask y Django.

Pero, en este inicio rápido, se usa la biblioteca de Falcon para experimentar el proceso de instalación de un paquete y la creación de la aplicación web desde el principio. En la actualidad, Visual Studio no incluye plantillas específicas de Falcon. Por simplicidad, en los pasos siguientes se instala Falcon en el entorno global predeterminado.

1. Expanda el nodo **Entornos de Python** en el proyecto para ver el entorno predeterminado para el proyecto.

    ![Explorador de soluciones en el que se muestra el entorno predeterminado](media/quickstart-python-02-default-environment.png)

1. Haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python...**. Este comando abre la ventana **Entornos de Python** por la pestaña **Paquetes**. Escriba "falcon" en el campo de búsqueda y seleccione **"instalación de PIP falcon" desde PyPI**. Acepte los mensajes de privilegios de administrador y observe el progreso en la ventana **Salida** de Visual Studio. (se le pedirá confirmación de elevación cuando la carpeta de paquetes del entorno global esté ubicada en un área protegida, como `c:\program files`).

    ![Instalación de la biblioteca Falcon](media/quickstart-python-03-install-package.png)

1. Una vez instalada, la biblioteca aparece en el entorno en el **Explorador de soluciones**, lo que significa que se puede usar en código de Python.

    ![Biblioteca Falcon instalada](media/quickstart-python-04-package-installed.png)

Para obtener más información sobre Falcon, visite [falconframework.org](https://falconframework.org/).

Tenga en cuenta que en lugar de instalar las bibliotecas en el entorno global, los desarrolladores suelen crear un "entorno virtual" en la que se instalan las bibliotecas de un proyecto específico. Muchas plantillas de proyecto de Python en Visual Studio incluyen un archivo `requirements.txt` en el que se enumeran las bibliotecas de las que depende la plantilla. La creación de un proyecto a partir de una de esas plantillas activa la creación de un entorno virtual en el que se instalan las bibliotecas. Para más información, vea [Entornos de Python: entornos virtuales](../python/managing-python-environments-in-visual-studio.md#creating-virtual-environments).

## <a name="add-a-code-file"></a>Agregar un archivo de código

Ahora está listo para agregar un poco de código de Python para implementar una aplicación web básica.

1. Haga clic con el botón derecho en el **Explorador de soluciones** y seleccione **Agregar > Nuevo elemento...**.

1. En el cuadro de diálogo que aparece, seleccione **Archivo de Python vacío**, asígnele el nombre `hello.py` y seleccione **Agregar**. Visual Studio abre automáticamente el archivo en una ventana del editor. (Por lo general, el comando **Agregar > Nuevo elemento...** es una excelente manera de agregar distintos tipos de archivos a un proyecto, dado que las plantillas de elementos suelen proporcionan código reutilizable útil).

1. Copie el siguiente código y péguelo en `hello.py`:

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. Después de pegar este código, es posible que, en Visual Studio, se muestre un subrayado ondulado debajo de `falcon` en la primera línea y también debajo de `wsgiref.simple.server` en la línea número 20. Estos indicadores aparecen cuando Visual Studio todavía está compilando la base de datos de IntelliSense para esos módulos.

Para más información sobre Falcon, vea el [Inicio rápido de Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Haga clic con el botón derecho en `hello.py` en el **Explorador de soluciones** y seleccione **Establecer como archivo de inicio**. El comando identifica el archivo de código que se va a iniciar en Python cuando se ejecuta la aplicación.

    ![Establecimiento del archivo de inicio para un proyecto en el Explorador de soluciones](media/quickstart-python-05-set-as-startup-file.png)

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto "Hello Python" y seleccione **Propiedades**. Después, haga clic en la pestaña **Depurar** y establezca la propiedad **Número de puerto** en `8080`. Este paso garantiza que Visual Studio inicia un explorador con `localhost:8080` en lugar de usar un puerto aleatorio.

1. Seleccione **Depurar > Iniciar sin depurar** (Ctrl+F5) para guardar los cambios en los archivos y ejecutar la aplicación.

1. Aparece la ventana Comandos con el mensaje "Iniciando servidor de aplicaciones web" y, después, se abre una ventana del explorador para `localhost:8080` en la que se puede ver el mensaje "Hello, Python!". La solicitud GET también aparece en la ventana de comandos.

    Si no se abre automáticamente un explorador, inicie el explorador que quiera y vaya a `localhost:8080`.

    Si solo ve el shell interactivo de Python en la ventana Comandos, o bien si esa ventana parpadea brevemente en la pantalla, asegúrese de haber establecido `hello.py` como archivo de inicio anteriormente en el paso 1.

1. Cierre la ventana Comandos para detener la aplicación. Después, cierre la ventana del explorador.

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena, ha completado este inicio rápido en el que ha obtenido información sobre el IDE de Visual Studio con Python. Para continuar con un tutorial más completo sobre Python en Visual Studio, incluido el uso de la ventana interactiva, depuración, visualización de datos y trabajar con Git, haga clic en el botón siguiente.

> [!div class="nextstepaction"]
> [Tutorial: Introducción a Python en Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

- Obtenga información sobre [Plantillas de aplicación web de Python en Visual Studio](../python/python-web-application-project-templates.md)
- Más información sobre la [depuración de Python](../python/debugging-python-in-visual-studio.md)
- Más información sobre el [IDE de Visual Studio](../ide/visual-studio-ide.md)
