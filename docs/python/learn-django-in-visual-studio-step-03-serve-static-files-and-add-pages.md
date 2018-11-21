---
title: 'Tutorial: Información acerca de Django en Visual Studio, paso 3'
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio, en particular la demostración de cómo atender archivos estáticos, agregar páginas a la aplicación y usar la herencia de plantilla.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: bea209e2d7cf751c66f3e627311a2985c79f55c3
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "52001300"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Paso 3. Atender archivos estáticos, agregar páginas y usar la herencia de plantilla

**Paso anterior: [Crear una aplicación de Django con vistas y plantillas de página](learn-django-in-visual-studio-step-02-create-an-app.md)**

En los pasos anteriores de este tutorial, ha aprendido a crear una aplicación de Django mínima con una sola página HTML independiente. Pero las aplicaciones web modernas están formadas normalmente por muchas páginas y usan recursos compartidos, como archivos CSS y JavaScript, para proporcionar un comportamiento y un estilo uniformes.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Usar plantillas de elementos de Visual Studio para agregar rápidamente nuevos archivos de distintos tipos con práctico código reutilizable (paso 3.1)
> - Configurar el proyecto de Django para atender archivos estáticos (paso 3.2)
> - Agregar páginas adicionales a la aplicación (paso 3.3)
> - Usar la herencia de plantilla para crear un encabezado y una barra de navegación que se use en varias páginas (paso 3.4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Paso 3.1: Familiarizarse con las plantillas de elemento

A medida que desarrolle una aplicación de Django, lo normal es que vaya agregando muchos más archivos Python, HTML, CSS y JavaScript. Para cada tipo de archivo (así como otros archivos como *web.config* que pueda necesitar para la implementación), Visual Studio ofrece prácticas [plantillas de elemento](python-item-templates.md) para empezar.

Para ver las plantillas disponibles, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la carpeta en la que desee crear el elemento y seleccione **Agregar** > **Nuevo elemento**:

![Cuadro de diálogo Agregar nuevo elemento en Visual Studio](media/django/step03-add-new-item-dialog.png)

Para usar una plantilla, seleccione la plantilla deseada, especifique un nombre para el archivo y seleccione **Aceptar**. La adición de un elemento de este modo agrega automáticamente el archivo al proyecto de Visual Studio y marca los cambios para el control de código fuente.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pregunta: ¿Cómo sabe Visual Studio qué plantillas de elemento debe ofrecer?

Respuesta: El archivo de proyecto de Visual Studio (*.pyproj*) contiene un identificador de tipo de proyecto que lo marca como un proyecto de Python. Visual Studio utiliza este identificador de tipo para mostrar solo aquellas plantillas de elementos que sean adecuadas para el tipo de proyecto. De esta manera, Visual Studio puede proporcionar un amplio conjunto de plantillas de elemento para muchos tipos de proyecto sin pedirle que los ordene cada vez.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Paso 3.2: Atender archivos estáticos desde la aplicación

En una aplicación web compilada con Python (con cualquier plataforma), los archivos de Python siempre se ejecutan en el servidor del host web y nunca se transmiten al equipo de un usuario. Otros archivos, sin embargo, como CSS y JavaScript, se usan exclusivamente por el explorador, por lo que el servidor host simplemente los ofrece tal cual cada vez que se soliciten. Estos archivos se denominan archivos "estáticos", y Django puede distribuirlos automáticamente sin tener que escribir ningún código.

Un proyecto de Django se configura de forma predeterminada para proporcionar archivos estáticos de la carpeta *static* de la aplicación, gracias a estas líneas en el archivo *settings.py* del proyecto de Django:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Puede organizar los archivos con cualquier estructura de carpetas de *static* que quiera y luego usar rutas de acceso relativas dentro de esa carpeta para hacer referencia a los archivos. Para mostrar este proceso, en los pasos siguientes se agrega un archivo CSS a la aplicación y luego se usa esa hoja de estilos en la plantilla *index.html*:

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **HelloDjangoApp** del proyecto de Visual Studio, seleccione **Agregar** > **Nueva carpeta** y ponga a la carpeta el nombre `static`.

1. Haga clic con el botón derecho en la carpeta **static** y seleccione **Agregar** > **Nuevo elemento**. En el cuadro de diálogo que aparece, seleccione la plantilla **Hoja de estilo**, ponga al archivo el nombre `site.css` y haga clic en **Aceptar**. El archivo **site.css** aparece en el proyecto y se abre en el editor. La estructura de carpetas debería ser similar a la de la imagen siguiente:

    ![Estructura de archivos estáticos tal y como se muestra en el Explorador de soluciones](media/django/step03-static-file-structure.png)

1. Reemplace el contenido de *site.css* por el código siguiente y guarde el archivo:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Reemplace el contenido del archivo *templates/HelloDjangoApp/index.html* de la aplicación por el código siguiente, que reemplaza el elemento `<strong>` usado en el paso 2 por un `<span>` que hace referencia a la clase de estilo `message`. El uso de una clase de estilo de este modo ofrece mucha más flexibilidad al aplicar estilo al elemento. (Si no ha movido *index.html* a una subcarpeta de *templates* al usar VS 2017 15.7 y versiones anteriores, vea [Template namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) [Espaciado entre nombres de plantilla] en el paso 2-4).

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Ejecute el proyecto y observe los resultados. Detenga el servidor cuando haya finalizado y confirme los cambios en el control de código fuente si lo desea (como se explica en [paso 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Pregunta: ¿Cuál es el fin de la etiqueta {% load staticfiles %}?

Respuesta: La línea `{% load staticfiles %}` se requiere antes de hacer referencia a los archivos estáticos en elementos como `<head>` y `<body>`. En el ejemplo que se muestra en esta sección, "staticfiles" hace referencia a un conjunto de etiquetas de plantilla de Django personalizado, que es lo que le permite usar la sintaxis `{% static %}` para hacer referencia a los archivos estáticos.  Sin `{% load staticfiles %}`, verá una excepción cuando se ejecute la aplicación.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pregunta: ¿Hay alguna convención para organizar los archivos estáticos?

Respuesta: Puede agregar otros archivos HTML, CSS y JavaScript a la carpeta *static* como quiera. Una forma habitual de organizar los archivos estáticos es crear subcarpetas denominadas *fonts*, *scripts* y *content* (para las hojas de estilos y cualquier otro archivo). En cada caso, no olvide incluir esas carpetas en la ruta de acceso relativa al archivo en las referencias de `{% static %}`.

## <a name="step-3-3-add-a-page-to-the-app"></a>Paso 3.3: Agregar una página a la aplicación

La adición de otra página a la aplicación implica lo siguiente:

- Agregar una función de Python que define la vista.
- Agregar una plantilla para el marcado de la página.
- Agregar el enrutamiento necesario al archivo *urls.py* del proyecto de Django.

Los pasos siguientes agregan una página de información al proyecto de "HelloDjangoApp" y los vínculos a esta página desde la página principal:

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **templates/HelloDjangoApp**, seleccione **Agregar** > **Nuevo elemento**, seleccione la plantilla de elemento **Página HTML**, ponga al archivo el nombre `about.html` y haga clic en **Aceptar**.

    > [!Tip]
    > Si el comando **Nuevo elemento** no aparece en el menú **Agregar**, asegúrese de que ha detenido el servidor para que Visual Studio salga del modo de depuración.

1. Reemplace el contenido de *about.html* por el siguiente marcado (reemplace el vínculo explícito a la página principal por una barra de navegación sencilla en el paso 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Abra el archivo *views.py* de la aplicación y agregue una función denominada `about` que use la plantilla:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Abra el archivo *urls.py* del proyecto de Django y agregue la línea siguiente a la matriz `urlPatterns`:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Abra el archivo *templates/HelloDjangoApp/index.html* y agregue la línea siguiente debajo del elemento `<body>` para vincular a la página Acerca de (de nuevo, reemplace este vínculo por una barra de navegación en el paso 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Guarde todos los archivos con el comando de menú **Archivo** > **Guardar todo** o simplemente presione **Ctrl**+**Mayús**+**S**. (Técnicamente, este paso no es necesario porque la ejecución del proyecto en Visual Studio guarda los archivos automáticamente. No obstante, es un comando que viene bien conocer).

1. Ejecute el proyecto para observar los resultados y compruebe la navegación entre las páginas. Cierre el servidor cuando haya finalizado.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Pregunta: He intentado utilizar "index" para el vínculo a la página principal, pero no funcionó. ¿Por qué?

Respuesta: Aunque la función de vista de *views.py* se denomina `index`, los patrones de enrutamiento de dirección URL del archivo *urls.py* del proyecto de Django no contienen una expresión regular que coincida con la cadena "index". Para que coincida con esa cadena, debe agregar otra entrada para el patrón `^index$`.

Como se muestra en la siguiente sección, es mucho mejor usar la etiqueta `{% url '<pattern_name>' %}` en la plantilla de página para hacer referencia al *nombre* de un modelo, en cuyo caso Django crea la dirección URL adecuada para su caso. Por ejemplo, reemplace `<div><a href="home">Home</a></div>` en *about.html* por `<div><a href="{% url 'index' %}">Home</a></div>`. El uso de "index" aquí funciona porque el primer patrón de dirección URL de *urls.py* se denomina, de hecho "index" (en virtud del argumento `name='index'`). También puede utilizar "home" para hacer referencia al segundo patrón.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Paso 3.4: Usar la herencia de plantilla para crear un encabezado y una barra de navegación

En lugar de tener vínculos de navegación explícitos en cada página, las aplicaciones web modernas suelen utilizan un encabezado de personalización de marca y una barra de navegación que proporciona los vínculos de página, los menús emergentes, etc. más importantes. Sin embargo, es poco práctico repetir el mismo código en cada plantilla de página para asegurarse de que el encabezado y la barra de navegación son los mismos en todas las páginas. Es preferible definir los elementos comunes de todas las páginas en un solo lugar.

El sistema de plantillas de Django ofrece dos formas de reutilizar elementos específicos a través de varias plantillas: la inclusión y la herencia.

- La *inclusión* son otras plantillas de página que se insertan en una ubicación específica de la plantillas de referencia mediante la sintaxis `{% include <template_path> %}`. También puede utilizar una variable si desea cambiar la ruta de acceso dinámicamente en el código. La inclusión se utiliza normalmente en el cuerpo de una página para incorporar la plantilla compartida en una ubicación específica de la página.

- La *herencia* utiliza `{% extends <template_path> %}` al principio de una plantilla de página para especificar una plantilla base compartida sobre la que construye a continuación la plantilla de referencia. La herencia se suele utilizar para definir un diseño, una barra de navegación y otras estructuras que se comparten entre las páginas de una aplicación, de manera que las plantillas de referencia solo tengan que agregar o modificar áreas específicas de la plantilla base denominadas *bloques*.

En ambos casos, `<template_path>` se refiere a la carpeta *templates* de la aplicación (`../` o `./` también son válidos).

Una plantilla base delimita los bloques usando las etiquetas `{% block <block_name> %}` y `{% endblock %}`. Si una plantilla de referencia utiliza etiquetas con el mismo nombre de bloque, su contenido de bloque reemplaza al de la plantilla base.

Los pasos siguientes muestran la herencia:

1. En la carpeta *templates/HelloDjangoApp* de la aplicación, cree un nuevo archivo HTML (con el menú contextual **Agregar** > **Nuevo elemento** o **Agregar** > **Página HTML**) denominado *layout.html* y reemplace su contenido por el siguiente marcado. Puede ver que esta plantilla contiene un bloque denominado "content" que es todo lo que tienen que reemplazar las páginas de referencia:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
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

1. Modifique *templates/HelloDjangoApp/index.html* para hacer referencia a la plantilla base y reemplace el bloque de contenido. Puede ver que, mediante la herencia, esta plantilla se simplifica:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modifique *templates/HelloDjangoApp/about.html* para que también haga referencia a la plantilla base y reemplace el bloque de contenido:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Ejecute el servidor para observar los resultados. Cierre el servidor cuando haya finalizado.

    ![Ejecución de la aplicación mostrando la barra de navegación](media/django/step03-nav-bar.png)

1. Dado que ha realizado cambios sustanciales en la aplicación, es de nuevo un buen momento para [confirmar los cambios en el control de código fuente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Usar la plantilla completa de Proyecto web de Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Publicación de la aplicación web en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Escribiendo su primera aplicación en Django, parte 3 (vistas)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Para conocer más funciones de las plantillas de Django, como el flujo de control, consulte [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (El lenguaje de plantilla de Django) (docs.djangoproject.com).
- Para obtener información detallada sobre el uso de la etiqueta `{% url %}`, consulte [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) dentro de [Built-in template tags and filters for Django templates reference](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (Etiquetas y filtros de plantilla integrados para referencia de plantillas de Django) (docs.djangoproject.com)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
