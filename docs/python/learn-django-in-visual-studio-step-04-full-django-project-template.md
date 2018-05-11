---
title: 'Tutorial: Información acerca de Django en Visual Studio, paso 4'
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio, en particular las características que ofrece la plantilla Proyecto web de Django.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9d48c8f86d29c990d254b2ed1d0adf471c24d6b8
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="tutorial-step-4-use-the-full-django-web-project-template"></a>Paso 4 del tutorial: Usar la plantilla completa Proyecto web de Django

**Paso anterior[: Atender archivos estáticos, agregar páginas y usar la herencia de plantilla](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Ahora que ha explorado los conceptos básicos de Django mediante la creación de una aplicación a partir de la plantilla "Proyecto web de Django en blanco" en Visual Studio, podrá comprender fácilmente la aplicación más completa que se genera mediante la plantilla "Proyecto web de Django".

En este paso, hará lo siguiente:

> [!div class="checklist"]
> - Crear una aplicación web de Django más completa mediante la plantilla "Proyecto web de Django" y examinar la estructura del proyecto (paso 4.1)
> - Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto, que consta de tres páginas que heredan de una plantilla de página base y emplea las bibliotecas estáticas de JavaScript, como jQuery y Bootstrap (paso 4.2)
> - Comprender el enrutamiento de direcciones URL que proporciona la plantilla (paso 4.3)

La plantilla también proporciona autenticación básica, que se explica en el paso 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Paso 4.1: Crear un proyecto a partir de la plantilla

1. En Visual Studio, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la solución "LearningDjango" que creó anteriormente en este tutorial y seleccione **Agregar** > **Nuevo proyecto**. (En caso de que desee utilizar una nueva solución, tendrá que seleccionar **Archivo** > **Nuevo** > **Proyecto**).

1. En el cuadro de diálogo del nuevo proyecto, busque y seleccione la plantilla "Proyecto web de Django", asigne al proyecto el nombre "DjangoWeb" y seleccione **Aceptar**.

1. Dado que la plantilla de nuevo incluye un archivo `requirements.txt`, Visual Studio le pregunta dónde desea instalar estas dependencias. Elija la opción **Install into a virtual environment** (Instalar en un entorno virtual) y, en el cuadro de diálogo **Agregar entorno virtual**, seleccione **Crear** para aceptar los valores predeterminados.

1. Una vez que Python finalice la configuración del entorno virtual, siga las instrucciones del `readme.html` que aparece para crear un superusuario de Django (esto es, un administrador). Simplemente haga clic con el botón derecho en el proyecto de Visual Studio y seleccione el comando **Python** > **Django Create Superuser** (Crear superusuario de Django); a continuación, siga las indicaciones. Asegúrese de registrar su nombre de usuario y contraseña cuando los use al ejecutar las características de autenticación de la aplicación.

1. Modifique la configuración para que el proyecto "DjangoWeb" sea el predeterminado para la solución de Visual Studio; para ello, haga clic con el botón derecho en ese proyecto en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**. El proyecto de inicio, que se muestra en negrita, es lo que ejecuta cuando se inicia el depurador.

    ![Explorador de soluciones mostrando el proyecto DjangoWeb como proyecto de inicio](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Seleccione **Depurar** > **Iniciar depuración** (F5) o use el botón **Servidor web** de la barra de herramientas para ejecutar el servidor:

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/django/run-web-server-toolbar-button.png)

1. La aplicación creada por la plantilla tiene tres páginas: una de inicio, otra de información y otra de contacto, por las que puede navegar con la barra de navegación. Tómese un par de minutos para examinar las diferentes partes de la aplicación. Para autenticarse en la aplicación a través del comando **Iniciar sesión**, use las credenciales de superusuario creadas anteriormente.

    ![Vista completa del explorador de la aplicación Proyecto web de Django](media/django/step04-full-app-desktop-view.png)

1. La aplicación creada por la plantilla "Proyecto web de Django" usa Bootstrap para el diseño con capacidad de respuesta que acoge los factores de los formatos móviles. Para ver esta capacidad de respuesta, cambie el tamaño del explorador a una vista estrecha para que el contenido se represente verticalmente y la barra de navegación se convierta en un icono de menú:

    ![Vista móvil (estrecha) de la aplicación Proyecto web de Django](media/django/step04-full-app-mobile-view.png)

1. Puede dejar la aplicación en ejecución para las secciones siguientes.

    Si desea detener la aplicación y [confirmar los cambios en el control de código fuente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), abra primero la página **Cambios** en **Team Explorer**, haga clic con el botón derecho en la carpeta del entorno virtual (probablemente `env`) y seleccione **Omitir estos elementos locales**.

### <a name="examine-what-the-template-creates"></a>Examen de lo que crea la plantilla

En el nivel más amplio, la plantilla "Proyecto web de Django" crea la siguiente estructura:

- Archivos en la raíz del proyecto:
  - `manage.py`, la utilidad administrativa de Django.
  - `db.sqlite3`, una base de datos de SQLite predeterminada.
  - `requirements.txt` que contiene una dependencia en Django 1.x.
  - `readme.html`, un archivo que se muestra en Visual Studio después de crear el proyecto. Como se indicó en la sección anterior, siga estas instrucciones para crear una cuenta de superusuario (administrador) para la aplicación.
- La carpeta `app` contiene todos los archivos de aplicación, incluidas vistas, modelos, pruebas, formularios, plantillas y archivos estáticos (vea el paso 4.2). Puede cambiar el nombre de esta carpeta para utilizar otro que le ayude a distinguirla mejor.
- La carpeta `DjangoWeb` (proyecto de Django) contiene los archivos de proyecto Django típicos: `__init.py__`, `settings.py`, `urls.py` y `wsgi.py`. Mediante el uso de la plantilla de proyecto, `settings.py` ya está configurado para la aplicación y el archivo de base de datos, y `urls.py` ya está configurado con las rutas a todas las páginas de aplicación, incluido el formulario de inicio de sesión.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pregunta: ¿Es posible compartir un entorno virtual entre los proyectos de Visual Studio?

Respuesta: Sí, pero hágalo siendo consciente de que es probable que proyectos diferentes usen paquetes diferentes con el tiempo y, por lo tanto, un entorno virtual compartido debe contener todos los paquetes de todos los proyectos que lo usan.

No obstante, para usar un entorno virtual existente, haga lo siguiente:

1. Cuando se le solicite instalar las dependencias en Visual Studio, seleccione la opción **Los instalaré de forma manual**.
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual existente**.
1. Vaya la carpeta que contiene el entorno virtual, selecciónela y luego elija **Aceptar**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Paso 4.2: Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto

Tal y como se observa cuando se ejecuta el proyecto, la aplicación contiene tres vistas: inicio, información y contacto. El código de estas vistas se encuentra en la carpeta `app/views`. Cada función de la vista simplemente llama a `django.shortcuts.render` con la ruta de acceso a una plantilla y un sencillo objeto de diccionario. Por ejemplo, la función `about` es quien controla la página de información:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Las plantillas se encuentran en la carpeta `templates/app` de la aplicación (habitualmente, cambiará el nombre de `app` al de la aplicación real). La plantilla base, `layout.html`, es la más extensa. Hace referencia a todos los archivos estáticos necesarios (JavaScript y CSS), define un bloque denominado "content" que otras páginas sobrescriben, y proporciona otro bloque denominado "scripts". Los siguientes extractos con anotaciones de `layout.html` muestran estas áreas específicas:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Las plantillas de página individuales, `about.html`, `contact.html` y `index.html`, y cada una de ellas amplía la plantilla base `layout.html`. `about.html` es la más sencilla y muestra las etiquetas `{% extends %}` y `{% block content %}`:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

`index.html` y `contact.html` utilizan la misma estructura y proporcionan contenido más largo en el bloque "content".

En la carpeta `templates/app` hay también una cuarta página `login.html`, junto con `loginpartial.html` que se traslada a `layout.html` con `{% include %}`. Estos archivos de plantilla se describen en el paso 5 sobre la autenticación.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Pregunta: ¿Es posible aplicar sangría a {% block %} y {% endblock %} en la plantilla de página de Django?

Respuesta: Sí, las plantillas de página de Django funcionan correctamente si aplica sangría a las etiquetas de bloque, quizás para alinearlas en sus elementos principales más adecuados. No se les aplica sangría en las plantillas de página generadas por la plantilla de proyecto de Visual Studio para que pueda ver claramente donde se colocan.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Paso 4.3: Comprender el enrutamiento de direcciones URL creado por la plantilla

El archivo `urls.py` del proyecto Django, tal como lo crea la plantilla "Proyecto web de Django", contiene el código siguiente:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Los primeros tres patrones de dirección URL se asignan directamente a las vistas `home`, `contact` y `about` en el archivo `views.py` de la aplicación. Los patrones `^login/$` y `^logout$`, por otra parte, usan las vistas de Django integradas en lugar de vistas definidas por la aplicación. Las llamadas al método `url` también incluyen datos adicionales para personalizar la vista. En el paso 5 se exploran estas llamadas.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Pregunta: En el proyecto que he creado, ¿por qué el patrón de dirección URL "about" utiliza "^about" en lugar de "^about$" como hemos visto aquí?

Respuesta: La falta de la "$" al final de la expresión regular se debe simplemente a un descuido en muchas de las versiones de la plantilla del proyecto. El patrón de dirección URL funciona perfectamente en una página denominada "about", pero sin el carácter "$" el patrón de dirección URL coincide también direcciones URL como "about=django", "about09876", "aboutoflaughter", etc. El carácter "$" al final se muestra aquí para crear un patrón de dirección URL que coincida *solo* con "about".

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Autenticación de los usuarios en Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="going-deeper"></a>Mayor profundización

- [Escribiendo su primera aplicación en Django, parte 4 (formas y vistas genéricas)](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learn-django](https://github.com/Microsoft/python-sample-vs-learn-django)