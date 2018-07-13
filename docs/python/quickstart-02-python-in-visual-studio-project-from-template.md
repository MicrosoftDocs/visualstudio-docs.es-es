---
title: 'Inicio rápido: Crear un proyecto de Python con una plantilla'
description: En este inicio rápido, creará un proyecto de Visual Studio para Python utilizando la plantilla integrada para una aplicación básica de Flask.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 046aeb3d43066dbe0bd28ef76036478efdbda49f
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "37057029"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Inicio rápido: Crear un proyecto de Python desde una plantilla en Visual Studio

Después de [instalar la compatibilidad con Python en Visual Studio 2017](installing-python-support-in-visual-studio.md), resulta fácil crear un nuevo proyecto de Python con una variedad de plantillas. En este inicio rápido, creará una aplicación sencilla de Flask mediante una plantilla. El proyecto resultante es similar al proyecto que crea manualmente a través de [Inicio rápido: usar Visual Studio para crear su primera aplicación web Python](../ide/quickstart-python.md).

1. Inicie Visual Studio 2017.

1. En la barra de menús superior seleccione **Archivo > Nuevo > Proyecto...** . Luego, en el cuadro de diálogo **Nuevo proyecto**, busque "flask en blanco", seleccione la plantilla "Proyecto web de Flask en blanco" en la lista del medio, asigne un nombre al proyecto y seleccione **Aceptar**:

    ![Creación de un nuevo proyecto con la plantilla Proyecto web de Flask en blanco](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio le mostrará un cuadro de diálogo que dice "Este proyecto necesita paquetes externos.". Este cuadro de diálogo aparece porque la plantilla incluye un archivo `requirements.txt` que especifica una dependencia en Flask. Visual Studio puede instalar automáticamente los paquetes y ofrece la opción de instalarlos en un *entorno virtual*. Se recomienda el uso de un entorno virtual frente a la instalación en un entorno global. Por tanto, seleccione **Install into a virtual environment** (Instalar en un entorno virtual) para continuar.

    ![Instalación de Flask en un entorno virtual](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio muestra el cuadro de diálogo **Agregar entorno virtual**. Acepte el valor predeterminado y seleccione **Crear**. A continuación, dé su consentimiento a las solicitudes de elevación.

    > [!Tip]
    > Cuando comienza un proyecto, es muy recomendable crear un entorno virtual de inmediato, como la mayoría de las plantillas de Visual Studio le invitan a hacer. Los entornos virtuales mantienen los requisitos exactos del proyecto a lo largo del tiempo, a medida que agrega y quita las bibliotecas. Luego puede generar fácilmente un archivo `requirements.txt`, que se utiliza para volver a instalar esas dependencias en otros equipos de desarrollo (como cuando se usa un control de código fuente) y al implementar el proyecto en un servidor de producción. Para más información sobre los entornos virtuales y sus ventajas, consulte [Uso de los entornos virtuales](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments) y [Administración de los paquetes necesarios con requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Después de que Visual Studio cree ese entorno, busque en el **Explorador de soluciones** para ver que tiene un archivo `app.py` junto con `requirements.txt`. Abra `app.py` para ver que la plantilla ha proporcionado código similar en [Inicio rápido: crear su primera aplicación web con Flask](../ide/quickstart-python.md), con varias secciones agregadas. Todo el código que se muestra a continuación se crea mediante la plantilla, por lo que no necesita pegar nada en `app.py`.

    El código comienza con las importaciones necesarias:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Después está la línea siguiente, que puede resultar útil cuando se implementa una aplicación en un host web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    A continuación está el decorador de ruta en una función simple que define una vista:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Por último está el código de inicio siguiente, que le permite establecer el host y el puerto a través de las variables de entorno, en lugar de codificarlos de forma rígida. Este código permite controlar fácilmente la configuración en máquinas de desarrollo y producción sin cambiar el código:

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

1. Seleccione **Depurar > Iniciar sin depurar** para ejecutar el programa y abrir un explorador en `localhost:5555`.

**Pregunta: ¿Qué otras plantillas de Python ofrece Visual Studio?**

**Respuesta**: Con la carga de trabajo de Python instalada, Visual Studio proporciona una variedad de plantillas de proyecto que incluyen las de los marcos web [Flask, Bottle y Django](../python/python-web-application-project-templates.md), servicios en la nube de Azure, diferentes escenarios de aprendizaje automático e incluso una plantilla para crear un proyecto a partir de una estructura de carpetas existente que contiene una aplicación de Python. Puede acceder a ellas a través del cuadro de diálogo **Archivo > Nuevo > Proyecto...**  seleccionando el nodo de lenguaje **Python** y sus nodos secundarios.

Visual Studio también proporciona una variedad de *plantillas de elemento* o archivo para crear rápidamente una clase de Python, un paquete de Python, una prueba unitaria de Python, archivos `web.config`, etc. Si tiene abierto un proyecto de Python, puede acceder a las plantillas de elemento a través del comando de menú **Proyecto > Agregar nuevo elemento**. Consulte la referencia sobre [plantillas de elemento](python-item-templates.md).

Mediante las plantillas puede ahorrar bastante tiempo al comenzar un proyecto o crear un archivo y también son una excelente manera de obtener información sobre diferentes tipos de aplicaciones y estructuras de código. Resulta útil invertir unos minutos en crear proyectos y elementos a partir de las diferentes plantillas para familiarizarse con lo que ofrecen.

**Pregunta: ¿Puedo usar también las plantillas de Cookiecutter?**

**Respuesta** : ¡Sí! De hecho, Visual Studio proporciona integración directa con Cookiecutter. Puede obtener información sobre esta utilidad en [Inicio rápido: crear un proyecto a partir de una plantilla de Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Trabajar con Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vea también

- [Manually identifying an existing Python interpreter](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment) (Identificación manual de un intérprete de Python existente).
- [Instalación de la compatibilidad con Python en Visual Studio 2015 y versiones anteriores](installing-python-support-in-visual-studio.md).
- [Ubicaciones de instalación](installing-python-support-in-visual-studio.md#install-locations).
