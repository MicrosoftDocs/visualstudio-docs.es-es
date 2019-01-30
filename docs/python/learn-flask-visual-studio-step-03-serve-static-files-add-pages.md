---
title: Información sobre el paso 3 del tutorial de Flask en Visual Studio, archivos estáticos y páginas
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Flask en el contexto de los proyectos de Visual Studio, en particular la demostración de cómo atender archivos estáticos, agregar páginas a la aplicación y usar la herencia de plantilla.
ms.date: 01/07/2019
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1b6464e48441f436b4f93fc8747972e334e768b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918543"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Paso 3: Proporcionar archivos estáticos, agregar páginas y usar la herencia de plantilla

**Paso anterior: [Creación de una aplicación de Flask con vistas y plantillas de página](learn-flask-visual-studio-step-02-create-app.md)**

En los pasos anteriores de este tutorial, ha aprendido a crear una aplicación de Flask mínima con una sola página HTML independiente. Pero las aplicaciones web modernas están formadas normalmente por muchas páginas y usan recursos compartidos, como archivos CSS y JavaScript, para proporcionar un comportamiento y un estilo uniformes.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Usar plantillas de elementos de Visual Studio para agregar rápidamente nuevos archivos de distintos tipos con práctico código reutilizable (paso 3.1)
> - Atender archivos estáticos desde el código (paso 3-2, opcional)
> - Agregar páginas adicionales a la aplicación (paso 3.3)
> - Usar la herencia de plantilla para crear un encabezado y una barra de navegación que se use en varias páginas (paso 3.4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Paso 3-1: Familiarizarse con las plantillas de elemento

A medida que desarrolle una aplicación de Flask, lo normal es que vaya agregando muchos más archivos Python, HTML, CSS y JavaScript. Para cada tipo de archivo (así como otros archivos como *web.config* que pueda necesitar para la implementación), Visual Studio ofrece prácticas [plantillas de elemento](python-item-templates.md) para empezar.

Para ver las plantillas disponibles, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la carpeta en la que desee crear el elemento y seleccione **Agregar** > **Nuevo elemento**:

![Cuadro de diálogo Agregar nuevo elemento en Visual Studio](media/flask/step03-add-new-item-dialog.png)

Para usar una plantilla, seleccione la plantilla deseada, especifique un nombre para el archivo y seleccione **Aceptar**. La adición de un elemento de este modo agrega automáticamente el archivo al proyecto de Visual Studio y marca los cambios para el control de código fuente.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cómo sabe Visual Studio qué plantillas de elemento debe ofrecer?

Respuesta: El archivo de proyecto de Visual Studio (*.pyproj*) contiene un identificador de tipo de proyecto que lo marca como un proyecto de Python. Visual Studio utiliza este identificador de tipo para mostrar solo aquellas plantillas de elementos que sean adecuadas para el tipo de proyecto. De esta manera, Visual Studio puede proporcionar un amplio conjunto de plantillas de elemento para muchos tipos de proyecto sin pedirle que los ordene cada vez.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Paso 3-2: Proporcionar archivos estáticos desde la aplicación

En una aplicación web compilada con Python (con cualquier plataforma), los archivos de Python siempre se ejecutan en el servidor del host web y nunca se transmiten al equipo de un usuario. Otros archivos, sin embargo, como CSS y JavaScript, se usan exclusivamente por el explorador, por lo que el servidor host simplemente los ofrece tal cual cada vez que se soliciten. Estos archivos se denominan archivos "estáticos", y Flask puede distribuirlos automáticamente sin tener que escribir ningún código. En los archivos HTML, por ejemplo, puede hacer referencia a archivos estáticos con una ruta de acceso relativa en el proyecto. En la primera sección de este paso se agrega un archivo CSS a la plantilla de página existente.

Cuando necesite proporcionar un archivo estático desde el código, por ejemplo, mediante una implementación de punto de conexión de API, Flask ofrece un cómodo método con el que hacer referencia a archivos mediante rutas de acceso relativas dentro de una carpeta denominada *static* (en la raíz del proyecto). En la segunda sección de este paso se muestra ese método usando un archivo de datos estático simple.

En cualquier caso, puede organizar los archivos en *static* como quiera.

### <a name="use-a-static-file-in-a-template"></a>Usar un archivo estático en una plantilla

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **HelloFlask** en el proyecto de Visual Studio, seleccione **Agregar** > **Nueva carpeta** y asigne a la carpeta el nombre `static`.

1. Haga clic con el botón derecho en la carpeta **static** y seleccione **Agregar** > **Nuevo elemento**. En el cuadro de diálogo que aparece, seleccione la plantilla **Hoja de estilo**, ponga al archivo el nombre `site.css` y haga clic en **Aceptar**. El archivo **site.css** aparece en el proyecto y se abre en el editor. La estructura de carpetas debería ser similar a la de la imagen siguiente:

    ![Estructura de archivos estáticos tal y como se muestra en el Explorador de soluciones](media/flask/step03-static-file-structure.png)

1. Reemplace el contenido de *site.css* por el código siguiente y guarde el archivo:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Reemplace el contenido del archivo *templates/index.html* de la aplicación por el código siguiente, que reemplaza el elemento `<strong>` usado en el paso 2 por un `<span>` que hace referencia a la clase de estilo `message`. El uso de una clase de estilo de este modo ofrece mucha más flexibilidad al aplicar estilo al elemento.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Ejecute el proyecto y observe los resultados. Detenga la aplicación cuando haya finalizado y confirme los cambios en el control de código fuente si quiere (como se explica en [paso 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Atender un archivo estático desde el código

Flask proporciona una función denominada `serve_static_file` a la que puede llamar desde el código para hacer referencia a cualquier archivo de la carpeta *static* del proyecto. El siguiente proceso crea un punto de conexión de API simple que devuelve un archivo de datos estáticos.

1. Si aún no lo ha hecho, cree una carpeta *static*: en el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **HelloFlask** del proyecto de Visual Studio, seleccione **Agregar** > **Nueva carpeta** y asigne a la carpeta el nombre `static`.

1. En la carpeta *static*, cree un archivo de datos JSON estático denominado *data.json* con el siguiente contenido (que son datos de ejemplo carentes de significado):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. En *views.py*, agregue una función con la ruta /api/data que devuelva el archivo de datos estático mediante el método `send_static_file`:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Ejecute la aplicación y vaya al punto de conexión /api/data para comprobar que se ha devuelto el archivo estático. Cuando haya terminado, detenga la aplicación.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Hay alguna convención para organizar los archivos estáticos?

Respuesta: Puede agregar otros archivos HTML, CSS y JavaScript a la carpeta *static* como quiera. Una forma habitual de organizar los archivos estáticos es crear subcarpetas denominadas *fonts*, *scripts* y *content* (para las hojas de estilos y cualquier otro archivo).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cómo se controlan las variables de dirección URL y los parámetros de consulta en una API?

Respuesta: Vea la respuesta en el paso 1-4 para [Pregunta: ¿Cómo trabaja Flask con las rutas de dirección URL de variables y con los parámetros de consulta?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Paso 3-3: Adición de una página a la aplicación

La adición de otra página a la aplicación implica lo siguiente:

- Agregar una función de Python que define la vista.
- Agregar una plantilla para el marcado de la página.
- Agregar el enrutamiento necesario al archivo *urls.py* del proyecto de Flask.

Los pasos siguientes agregan una página de información al proyecto de "HelloFlask" y los vínculos a esta página desde la página principal:

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **templates**, seleccione **Agregar** > **Nuevo elemento**, seleccione la plantilla de elemento **Página HTML**, ponga al archivo el nombre `about.html` y haga clic en **Aceptar**.

    > [!Tip]
    > Si el comando **Nuevo elemento** no aparece en el menú **Agregar**, asegúrese de que ha detenido la aplicación para que Visual Studio salga del modo de depuración.

1. Reemplace el contenido de *about.html* por el siguiente marcado (reemplace el vínculo explícito a la página principal por una barra de navegación sencilla en el paso 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Abra el archivo *views.py* de la aplicación y agregue una función denominada `about` que use la plantilla:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Abra el archivo *templates/index.html* y agregue la siguiente línea dentro del elemento `<body>` que se va a vincular a la página Acerca de (de nuevo, reemplace este vínculo por una barra de navegación en el paso 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Guarde todos los archivos con el comando de menú **Archivo** > **Guardar todo** o simplemente presione **Ctrl**+**Mayús**+**S**. (Técnicamente, este paso no es necesario porque la ejecución del proyecto en Visual Studio guarda los archivos automáticamente. No obstante, es un comando que viene bien conocer).

1. Ejecute el proyecto para observar los resultados y compruebe la navegación entre las páginas. Detenga la aplicación cuando haya finalizado.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Importa en Flask el nombre de una función de página?

Respuesta: No, porque es el decorador `@app.route` el que determina las direcciones URL para las que Flask llama a la función para generar una respuesta. Los desarrolladores suelen hacer coincidir el nombre de la función con la ruta, aunque no es algo obligatorio.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Paso 3-4: Uso de la herencia de plantilla para crear un encabezado y una barra de navegación

En lugar de tener vínculos de navegación explícitos en cada página, las aplicaciones web modernas suelen utilizan un encabezado de personalización de marca y una barra de navegación que proporciona los vínculos de página, los menús emergentes, etc. más importantes. Sin embargo, es poco práctico repetir el mismo código en cada plantilla de página para asegurarse de que el encabezado y la barra de navegación son los mismos en todas las páginas. Es preferible definir los elementos comunes de todas las páginas en un solo lugar.

El sistema de plantillas de Flask (Jinja de forma predeterminada) ofrece dos formas de reutilizar elementos específicos a través de varias plantillas: la inclusión y la herencia.

- La *inclusión* son otras plantillas de página que se insertan en una ubicación específica de la plantillas de referencia mediante la sintaxis `{% include <template_path> %}`. También puede utilizar una variable si desea cambiar la ruta de acceso dinámicamente en el código. La inclusión se utiliza normalmente en el cuerpo de una página para incorporar la plantilla compartida en una ubicación específica de la página.

- La *herencia* utiliza `{% extends <template_path> %}` al principio de una plantilla de página para especificar una plantilla base compartida sobre la que construye a continuación la plantilla de referencia. La herencia se suele utilizar para definir un diseño, una barra de navegación y otras estructuras que se comparten entre las páginas de una aplicación, de manera que las plantillas de referencia solo tengan que agregar o modificar áreas específicas de la plantilla base denominadas *bloques*.

En ambos casos, `<template_path>` se refiere a la carpeta *templates* de la aplicación (`../` o `./` también son válidos).

Una plantilla base delimita los *bloques* mediante las etiquetas `{% block <block_name> %}` y `{% endblock %}`. Si una plantilla de referencia utiliza etiquetas con el mismo nombre de bloque, su contenido de bloque reemplaza al de la plantilla base.

Los pasos siguientes muestran la herencia:

1. En la carpeta *templates* de la aplicación, cree un nuevo archivo HTML (con el menú contextual **Agregar** > **Nuevo elemento** o **Agregar** > **Página HTML**) denominado *layout.html* y reemplace su contenido por el siguiente marcado. Puede ver que esta plantilla contiene un bloque denominado "content" que es todo lo que tienen que reemplazar las páginas de referencia:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Agregue los estilos siguientes al archivo *static/site.css* de la aplicación (en este tutorial no se está intentando mostrar un diseño con capacidad de respuesta; estos estilos simplemente sirven para generar un resultado interesante):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Modifique *templates/index.html* para hacer referencia a la plantilla base y reemplace el bloque de contenido. Puede ver que, mediante la herencia, esta plantilla se simplifica:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modifique *templates/about.html* para hacer también referencia a la plantilla base y reemplace el bloque de contenido:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Ejecute el servidor para observar los resultados. Cierre el servidor cuando haya finalizado.

    ![Ejecución de la aplicación mostrando la barra de navegación](media/flask/step03-nav-bar.png)

1. Dado que ha efectuado cambios sustanciales en la aplicación, vuelve a ser un buen momento para [confirmar los cambios en el control de código fuente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Usar la plantilla de proyecto web completa de Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Publicación de la aplicación web en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Para ver más funcionalidades de las plantillas de Jinja, como el flujo de control, vea la [documentación del diseñador de plantillas de Jinja](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Para obtener información detallada sobre cómo usar `url_for`, vea [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) en la documentación de objetos de aplicación de Flask (flask.pocoo.org)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
