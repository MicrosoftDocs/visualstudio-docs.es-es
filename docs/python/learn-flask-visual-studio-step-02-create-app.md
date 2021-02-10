---
title: Información sobre el paso 2 del tutorial de Flask en Visual Studio, vistas y plantillas
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Flask en el contexto de los proyectos de Visual Studio, en particular los pasos para crear una aplicación y usar vistas y plantillas.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e9d55d9c1c22edea1ff826b23beb6d0ec6b392c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942417"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Paso 2: Creación de una aplicación de Flask con vistas y plantillas de página

**Paso anterior: [Creación de una solución y un proyecto de Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Lo que ha conseguido en el paso 1 de este tutorial es una aplicación de Flask con una página y todo el código en un único archivo. Para facilitar un desarrollo futuro, es mejor refactorizar el código y crear una estructura para las plantillas de página. En concreto, debe separar el código de las vistas de la aplicación de otros aspectos, como el código de inicio.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Refactorizar el código de la aplicación para separar las vistas del código de inicio (paso 2-1)
> - Representar una vista mediante una plantilla de página (paso 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Paso 2-1: Refactorización del proyecto para admitir desarrollo adicional

En el código creado por la plantilla "Proyecto web de Flask en blanco" tiene un archivo único *app.py* que contiene el código de inicio junto con una sola vista. Para facilitar un desarrollo futuro de una aplicación que tiene varias vistas y plantillas, es mejor separar estos elementos.

1. En la carpeta del proyecto, cree una carpeta de aplicación llamada `HelloFlask` (haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Agregar** > **Nueva carpeta**).

2. En la carpeta *HelloFlask*, cree un archivo denominado *\_\_init\_\_.py* con el siguiente contenido que crea la instancia `Flask` y carga las vistas de la aplicación (que se crean en el siguiente paso):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. En la carpeta *HelloFlask*, cree un archivo denominado *views.py* con el siguiente contenido. El nombre *views.py* es importante porque se ha usado `import HelloFlask.views` en *\_\_init\_\_.py*. Verá un error en tiempo de ejecución si los nombres no coinciden.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Además de cambiar el nombre de la función y la ruta a `home`, este código contiene el código de representación de la página de *app.py* e importa el objeto `app` que se declara en *\_\_init\_\_.py*.

4. Cree una subcarpeta en *HelloFlask* denominada *templates*, que de momento estará vacía.

5. En la carpeta raíz del proyecto, cambie el nombre de *app.py* por *runserver.py* y haga coincidir el contenido con el siguiente código:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. La estructura del proyecto debe parecerse a la siguiente imagen:

    ![Estructura del proyecto después de refactorizar el código](media/flask/step02-project-structure.png)

7. Seleccione **Depurar** > **Iniciar depuración** (**F5**) o use el botón **Servidor web** de la barra de herramientas (el explorador puede variar) para que se inicie la aplicación y se abra un explorador. Pruebe las rutas de dirección URL / y /home.

8. También puede establecer puntos de interrupción en distintas partes del código y reiniciar la aplicación para seguir la secuencia de inicio. Por ejemplo, establezca un punto de interrupción en las primeras líneas de *runserver.py* y *HelloFlask\_* init *_.py* y en la línea `return "Hello Flask!"` de *views.py*. Luego, reinicie la aplicación (**Depurar** > **Reiniciar**, **Ctrl**+**Mayús**+**F5**, o el botón de la barra de herramientas que se muestra a continuación) y recorra el código (**F10**) o ejecútelo desde cada punto de interrupción mediante **F5**.

    ![Botón Reiniciar en la barra de herramientas de depuración en Visual Studio](media/debugging-restart-toolbar-button.png)

9. Cuando haya terminado, detenga la aplicación.

### <a name="commit-to-source-control"></a>Confirmación en el control de código fuente

Dado que ha realizado cambios en el código y ha probado que funcionan correctamente, ahora es un buen momento para revisar y confirmar los cambios en el control de código fuente. Los pasos posteriores de este tutorial le recuerdan los momentos adecuados para volver a confirmar el control de código fuente, y le remiten a esta sección.

1. Seleccione el botón de cambios de la parte inferior de Visual Studio (en un círculo abajo), que le lleva a **Team Explorer**.

    ![Botón de cambios de control de código fuente en la barra de estado de Visual Studio](media/flask/step02-source-control-changes-button.png)

1. En **Team Explorer**, escriba un mensaje de confirmación como "Refactorizar código" y seleccione **Confirmar todo**. Una vez que se haya completado la confirmación, verá un mensaje **Confirmar \<hash> de creación local. Sincronizar para compartir los cambios con el servidor.** Si desea insertar los cambios en el repositorio remoto, seleccione **Sincronizar** y luego **Insertar** en **Confirmaciones de salida**. También puede acumular varias confirmaciones locales antes de insertar en la instancia remota.

    ![Inserción de confirmaciones en instancia remota en Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Con qué frecuencia se debe confirmar en el control de código fuente?

Respuesta: La confirmación de los cambios en el control de código fuente crea un registro en el registro de cambios y un punto al que puede revertir el repositorio si es necesario. También se puede examinar cada confirmación para ver los cambios concretos. Dado que las confirmaciones en Git son asequibles, es mejor hacer confirmaciones frecuentes que acumular muchos cambios en una confirmación. Evidentemente, no es necesario confirmar todos los cambios en archivos concretos. Por lo general se efectúa una confirmación al agregar una característica, al cambiar una estructura como ha hecho en este paso o al llevar a cabo ciertas refactorizaciones de código. Compruebe también con otros usuarios del equipo la granularidad de las confirmaciones que mejor funcionen para cada uno.

La frecuencia con la que confirme y la frecuencia con la que se envían las confirmaciones a un repositorio remoto son dos cuestiones diferentes. Se pueden acumular varias confirmaciones en el repositorio local antes de enviarlas al repositorio remoto. Una vez más, la frecuencia con la que confirme dependerá de cómo quiera administrar su equipo el repositorio.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Paso 2-2: Uso de una plantilla para representar una página

La función `home` que tiene de momento en *views.py* solo genera una respuesta HTTP en texto sin formato para la página. Pero la mayoría las páginas web reales responden con páginas HTML enriquecidas que a menudo incorporan datos en directo. De hecho, la razón principal para definir una vista mediante una función es la generación de contenido de forma dinámica.

Como el valor devuelto para la vista es una cadena, puede crear cualquier código HTML que quiera dentro de una cadena mediante contenido dinámico, pero dado que es mejor separar el marcado de los datos, es mucho mejor colocarlo en una plantilla y mantener los datos en el código.

1. Para empezar, edite *views.py* para que contenga el siguiente código que usa HTML insertado para la página con algún contenido dinámico:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Ejecute la aplicación y actualice la página varias veces para comprobar que se actualice la fecha y la hora. Cuando haya terminado, detenga la aplicación.

1. Para convertir la representación de la página para usar una plantilla, cree un archivo denominado *index.html* en la carpeta *templates* con el siguiente contenido, donde `{{ content }}` es un marcador de posición o un token de reemplazo (también denominado *variable de plantilla*) para el que se proporciona un valor en el código:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modifique la función `home` para usar `render_template` para cargar la plantilla y proporcione un valor para "content", lo cual se hace usando un argumento con nombre que coincida con el nombre del marcador de posición. Flask busca automáticamente plantillas en la carpeta *templates*, así que la ruta de acceso a la plantilla es relativa a esa carpeta:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Ejecute la aplicación para ver los resultados y observe que el HTML insertado del valor `content` no se representa *como* HTML porque el motor de plantillas (Jinja) efectúa un escape automático del contenido HTML. El escape automático evita vulnerabilidades accidentales en los ataques por inyección de código: los desarrolladores suelen recopilar información de una página y emplearla como valor en otra mediante un marcador de posición de plantilla. El escape también sirve como recordatorio de que es mejor conservar el HTML fuera del código.

    En consecuencia, compruebe que *templates\index.html* contenga distintos marcadores de posición para cada sección de los datos dentro del marcado:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Luego, actualice la función `home` para proporcionar valores para todos los marcadores de posición:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Vuelva a ejecutar la aplicación para ver la salida correctamente representada.

    ![Ejecución de la aplicación con la plantilla](media/flask/step02-result.png)

1. Confirme los cambios en el control de código fuente y actualice su repositorio remoto, si quiere, tal y como se describe en el [paso 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Las plantillas de página deben estar en un archivo independiente?

Respuesta: Aunque las plantillas normalmente se guardan en archivos HTML independientes, también se puede usar una plantilla insertada. No obstante, se recomienda usar un archivo independiente para mantener una separación clara entre código y marcado.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Deben usar las plantillas la extensión de archivo .html?

Respuesta: La extensión *.html* para los archivos de plantilla de página es completamente opcional, ya que siempre puede identificar la ruta de acceso exacta relativa al archivo en el primer argumento de la función `render_template`. Pero Visual Studio (y otros editores) normalmente ofrecen características como la finalización de código y el coloreado de sintaxis con archivos *.html*, lo que compensa con creces el hecho de que las plantillas de página no sean estrictamente HTML.

De hecho, cuando está trabajando con un proyecto de Flask, Visual Studio detecta automáticamente si el archivo HTML que está editando es realmente una plantilla de Flask y proporciona algunas características de autocompletar. Por ejemplo, al comenzar a escribir un comentario de plantilla de página de Flask, `{#`, Visual Studio proporciona automáticamente los caracteres `#}` de cierre. Los comandos **Selección con comentarios** y **Selección sin comentarios** (en el menú **Editar** > **Opciones avanzadas** y en la barra de herramientas) también utilizan comentarios de plantilla en lugar de comentarios HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Las plantillas se pueden organizar en más subcarpetas?

Respuesta: Sí, se pueden usar subcarpetas y luego hacer referencia a la ruta de acceso relativa en *templates* en las llamadas a `render_template`. Es una excelente manera de crear espacios de nombres de forma efectiva para las plantillas.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Atender archivos estáticos, agregar páginas y usar la herencia de plantilla](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Inicio rápido de Flask: Representación de plantillas](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
