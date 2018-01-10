---
title: "Inicio rápido: usar Visual Studio para crear su primera aplicación web Python | Microsoft Docs"
ms.custom: 
ms.date: 12/1/2017"
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: bf0a6e187a98a03d3beed33537fe5244ecd5d35d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Inicio rápido: usar Visual Studio para crear su primera aplicación web Python

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web Python. Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

## <a name="create-the-project"></a>Crear el proyecto

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo > Nuevo > Proyecto...**.

1. En el cuadro de diálogo **Nuevo proyecto**, en el panel de la izquierda, expanda **Otros lenguajes** y después seleccione **Python**. En el panel central, elija **Proyecto web**, asigne al proyecto un nombre como "HelloPython" y luego haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto de Python, cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas > Obtener herramientas y características...** para abrir el instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Python** y, luego, haga clic en **Modificar**.

    ![Carga de trabajo de desarrollo de Python en el instalador de Visual Studio](../python/media/installation-python-workload.png)

1. El nuevo proyecto se abre en el panel de la derecha del **Explorador de soluciones**. En este momento el proyecto está vacío porque no contiene ningún otro archivo.

    ![Explorador de soluciones con el proyecto vacío recién creado](media/quickstart-python-01-empty-project.png)

## <a name="install-the-falcon-library"></a>Instalar la biblioteca Falcon

En las aplicaciones web de Python casi siempre se usa una de las muchas bibliotecas de Python disponibles para controlar detalles de bajo nivel como el enrutamiento de solicitudes web y la forma de las respuestas. La carga de trabajo de desarrollo de Python en Visual Studio proporciona [una variedad de plantillas para aplicaciones web](../python/template-web.md) generadas en torno a las bibliotecas Bottle, Flask y Django.

Pero en este tutorial rápido, se usa una biblioteca diferente, [Falcon](https://falconframework.org/), para experimentar el proceso de instalación de un paquete y la creación de la aplicación web desde el principio. Por simplicidad, en los pasos siguientes se instala Falcon en el entorno global predeterminado.

1. Expanda el nodo **Entornos de Python** en el proyecto para ver el entorno predeterminado para el proyecto.

    ![Explorador de soluciones en el que se muestra el entorno predeterminado](media/quickstart-python-02-default-environment.png)

1. Haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python...**. Este comando abre la ventana **Entornos de Python** por la pestaña **Paquetes**. Escriba "falcon" en el campo de búsqueda y seleccione **"instalación de PIP falcon" desde PyPI**. Acepte los mensajes de privilegios de administrador y observe el progreso en la ventana **Salida** de Visual Studio.

    ![Instalación de la biblioteca Falcon](media/quickstart-python-03-install-package.png)

1. Una vez instalada, la biblioteca aparece en el entorno en el **Explorador de soluciones**, lo que significa que se puede usar en código de Python.

    ![Biblioteca Falcon instalada](media/quickstart-python-04-package-installed.png)

Tenga en cuenta que en lugar de instalar las bibliotecas en el entorno global, los desarrolladores suelen crear un "entorno virtual" en la que se instalan las bibliotecas de un proyecto específico. Muchas plantillas de proyecto de Python en Visual Studio incluyen un archivo `requirements.txt` en el que se enumeran las bibliotecas de las que depende la plantilla. La creación de un proyecto a partir de una de esas plantillas activa la creación de un entorno virtual en el que se instalan las bibliotecas. Para más información, vea [Entornos de Python: entornos virtuales](../python/python-environments.md#virtual-environments).

## <a name="add-a-code-file"></a>Agregar un archivo de código

Ahora está listo para agregar un poco de código de Python para implementar una aplicación web básica.

1. Haga clic con el botón derecho en el **Explorador de soluciones** y seleccione **Agregar > Nuevo elemento...**. En el cuadro de diálogo que aparece, seleccione **Archivo de Python vacío**, asígnele el nombre `hello.py` y haga clic **Aceptar**. Visual Studio abre automáticamente el archivo en una ventana del editor. (Por lo general, el comando **Agregar > Nuevo elemento...** es una excelente manera de agregar distintos tipos de archivos a un proyecto, dado que las plantillas de elementos suelen proporcionan código reutilizable útil).

1. Copie y pegue, o escriba el código siguiente en `hello.py`:

    ```python
    import falcon
    api = falcon.API()

    # In Falcon, define a class for each resource; the on_get 
    # method then handles any GET requests.

    class HelloResource:
        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to the HelloResource
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

Para más información sobre Falcon, vea el [Inicio rápido de Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Haga clic con el botón derecho en `hello.py` en el **Explorador de soluciones** y seleccione **Establecer como archivo de inicio**. El comando identifica el archivo de código que se va a iniciar en Python cuando se ejecuta la aplicación.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto "Hello Python" y seleccione **Propiedades**. Después, haga clic en la pestaña **Depurar** y establezca la propiedad **Número de puerto** en `8080`. Este paso garantiza que Visual Studio inicia un explorador con `localhost:8080` en lugar de usar un puerto aleatorio.

1. Seleccione **Depurar > Iniciar sin depurar** (Ctrl+F5) para guardar los cambios en los archivos y ejecutar la aplicación.

1. Aparece una ventana de comandos con el mensaje "Iniciando servidor de aplicaciones web" y, después, se abre una ventana del explorador por `localhost:8080` donde se puede ver el mensaje "Hello, Python!". La solicitud GET también aparece en la ventana de comandos. (Si ve solo el shell interactivo de Python en la ventana de comandos, o si esa ventana parpadea brevemente en la pantalla, asegúrese de establecer `hello.py` como el archivo de inicio en el paso 1 anterior).

1. Cierre la ventana de comandos para detener la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial rápido, en el que ha obtenido información sobre el IDE de Visual Studio con Python. Para continuar con un tutorial más completo sobre Python en Visual Studio, incluido el uso de la ventana interactiva, depuración, visualización de datos y trabajar con Git, haga clic en el botón siguiente.

> [!div class="nextstepaction"]
> [Tutorial: Introducción a Python en Visual Studio](../python/vs-tutorial-01-01.md).

- Obtenga información sobre [Plantillas de aplicación web de Python en Visual Studio](../python/template-web.md)
- Más información sobre el [IDE de Visual Studio](../ide/visual-studio-ide.md)
- Obtenga información sobre cómo usar el [depurador de Visual Studio](../debugger/debugger-feature-tour.md)