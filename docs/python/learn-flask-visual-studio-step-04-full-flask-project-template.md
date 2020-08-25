---
title: Información sobre el paso 4 del tutorial de Flask en Visual Studio, Plantillas de proyecto web
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Flask en el contexto de los proyectos de Visual Studio, en particular las características que ofrecen las plantillas Proyecto web de Flask y Proyecto web de Flask/Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fa59197e584c6c8062c13354178f883b60b36442
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250571"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Paso 4. Usar la plantilla de proyecto web completa de Flask

**Paso anterior[: Atender archivos estáticos, agregar páginas y usar la herencia de plantilla](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Ahora que ha explorado los conceptos básicos de Flask mediante la creación de una aplicación a partir de la plantilla "Proyecto web de Flask en blanco" en Visual Studio, podrá comprender fácilmente la aplicación más completa que se genera mediante la plantilla "Proyecto web de Flask".

En este paso, hará lo siguiente:

> [!div class="checklist"]
> - Crear una aplicación web de Flask más completa mediante la plantilla "Proyecto web de Flask" y examinar la estructura del proyecto (paso 4-1)
> - Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto, que consta de tres páginas que heredan de una plantilla de página base y emplea las bibliotecas estáticas de JavaScript, como jQuery y Bootstrap (paso 4.2)
> - Comprender el enrutamiento de direcciones URL que proporciona la plantilla (paso 4.3)

Este artículo también se aplica a la plantilla "Proyecto web de Flask/Jade", que genera una aplicación idéntica a la de "Proyecto web de Flask" con el motor de plantillas de Jade en vez del de Jinja. Al final de este artículo se incluye más información detallada.

## <a name="step-4-1-create-a-project-from-the-template"></a>Paso 4.1: Crear un proyecto a partir de la plantilla

1. En Visual Studio, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la solución **LearningFlask** creada anteriormente en este tutorial y seleccione **Agregar** > **Nuevo proyecto**. (En caso de que desee utilizar una nueva solución, tendrá que seleccionar **Archivo** > **Nuevo** > **Proyecto**).

1. En el cuadro de diálogo del nuevo proyecto, busque y seleccione la plantilla **Proyecto web de Flask**, asigne al proyecto el nombre "FlaskWeb" y haga clic en **Aceptar**.

1. Dado que la plantilla de nuevo incluye un archivo *requirements.txt*, Visual Studio le pregunta dónde instalar esas dependencias. Elija la opción **Install into a virtual environment** (Instalar en un entorno virtual) y, en el cuadro de diálogo **Agregar entorno virtual**, seleccione **Crear** para aceptar los valores predeterminados.

1. Cuando Visual Studio termine de configurar el entorno virtual, establezca el proyecto **FlaskWeb** como predeterminado para la solución de Visual Studio. Para ello, haga clic con el botón derecho en ese proyecto en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**. El proyecto de inicio, que se muestra en negrita, es lo que ejecuta cuando se inicia el depurador.

    ![Explorador de soluciones mostrando el proyecto web de Flask como proyecto de inicio](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Seleccione **Depurar** > **Iniciar depuración** (**F5**) o use el botón **Servidor web** de la barra de herramientas para ejecutar el servidor:

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. La aplicación creada por la plantilla tiene tres páginas: una de inicio, otra de información y otra de contacto, por las que puede navegar con la barra de navegación. Tómese un par de minutos para examinar las diferentes partes de la aplicación. Para autenticarse en la aplicación a través del comando **Iniciar sesión**, use las credenciales de superusuario creadas anteriormente.

    ![Vista completa del explorador de la aplicación Proyecto web de Flask](media/flask/step04-full-app-desktop-view.png)

1. La aplicación creada por la plantilla "Proyecto web de Flask" usa Bootstrap para el diseño con capacidad de respuesta que acoge los factores de los formatos móviles. Para ver esta capacidad de respuesta, cambie el tamaño del explorador a una vista estrecha para que el contenido se represente verticalmente y la barra de navegación se convierta en un icono de menú:

    ![Vista móvil (estrecha) de la aplicación Proyecto web de Flask](media/flask/step04-full-app-mobile-view.png)

1. Puede dejar la aplicación en ejecución para las secciones siguientes.

    Si quiere detener la aplicación y [confirmar los cambios en el control de código fuente](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), primero abra la página **Cambios** en **Team Explorer**, haga clic con el botón derecho en la carpeta del entorno virtual (probablemente **env**) y seleccione **Omitir estos elementos locales**.

### <a name="examine-what-the-template-creates"></a>Examen de lo que crea la plantilla

La plantilla de "Proyecto web de Flask" crea la estructura siguiente. El contenido es muy similar a lo que ha creado en los pasos anteriores. La diferencia está en que la plantilla "Proyecto web de Flask" contiene más estructura de la carpeta *static* porque incluye jQuery y Bootstrap para un diseño dinámico. La plantilla también agrega una página de contacto. En general, si ha seguido los pasos anteriores de este tutorial, todo el contenido de la plantilla debería resultarle familiar.

- Archivos en la raíz del proyecto:
  - *runserver.py*, un script para ejecutar la aplicación en un servidor de desarrollo.
  - *requirements.txt*, que contiene una dependencia en Flask 0.x.
- La carpeta *FlaskWeb* contiene todos los archivos de la aplicación:
  - *\_\_init.py\_\_* marca el código de la aplicación como un módulo de Python, crea el objeto de Flask e importa las vistas de la aplicación.
  - *views.py* contiene el código para representar páginas.
  - La carpeta *static* contiene subcarpetas denominadas *content* (archivos CSS), *fonts* (archivos de fuentes) y *scripts* (archivos de JavaScript).
  - La carpeta *templates* contiene una plantilla base *layout.html* junto con *about.html*, *contact.html* e *index.HTML* para páginas específicas que amplían *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pregunta: ¿Es posible compartir un entorno virtual entre los proyectos de Visual Studio?

Respuesta: Sí, pero hágalo siendo consciente de que es probable que proyectos diferentes usen paquetes diferentes con el tiempo y, por lo tanto, un entorno virtual compartido debe contener todos los paquetes de todos los proyectos que lo usan.

No obstante, para usar un entorno virtual existente, haga lo siguiente:

1. Cuando se le solicite instalar las dependencias en Visual Studio, seleccione la opción **Los instalaré de forma manual**.
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual existente**.
1. Vaya la carpeta que contiene el entorno virtual, selecciónela y luego elija **Aceptar**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Paso 4.2: Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto

Tal y como se observa cuando se ejecuta el proyecto, la aplicación contiene tres vistas: inicio, información y contacto. El código de estas vistas se encuentra en *FlaskWeb/views.py*. Cada función de vista llama a `flask.render_template` con la ruta de acceso a una plantilla y una lista variable de argumentos para los valores que se van a asignar a la plantilla. Por ejemplo, la página Acerca de se gestiona con la función `about` (cuyo decorador proporciona el enrutamiento de la dirección URL):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

Las funciones `home`y `contact` son prácticamente idénticas, con decoradores similares y argumentos algo diferentes.

Las plantillas se encuentran en la carpeta *templates* de la aplicación. La plantilla base, *layout.html*, es la más extensa. Hace referencia a todos los archivos estáticos necesarios (JavaScript y CSS), define un bloque denominado "content" que otras páginas sobrescriben, y proporciona otro bloque denominado "scripts". Los siguientes extractos con anotaciones de *layout.html* muestran estas áreas específicas:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

Las plantillas de página individuales, *about.html*, *contact.html* e *index.html*, amplían la plantilla base *layout.html*. *about.html* es la más sencilla y muestra las etiquetas `{% extends %}` y `{% block content %}`:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* y *contact.html* usan la misma estructura y proporcionan contenido más largo en el bloque "content".

## <a name="the-flaskjade-web-project-template"></a>Plantilla de proyecto web de Flask/Jade

Como se ha indicado al principio de este artículo, Visual Studio proporciona una plantilla "Proyecto web de Flask/Jade", que crea una aplicación que es visualmente idéntica a lo que genera "Proyecto web de Flask". La principal diferencia es que usa el motor de plantillas de Jade, que es una extensión de Jinja que implementa los mismos conceptos con un lenguaje más conciso. En concreto, Jade usa, por ejemplo, palabras clave en lugar de etiquetas entre delimitadores {% %} y permite hacer referencia a estilos CSS y elementos HTML mediante palabras clave.

Para habilitar Jade, la plantilla de proyecto incluye primero el paquete pyjade en *requirements.txt*.

El archivo *\_\_init\_\_.py* de la aplicación contiene una línea para

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

En la carpeta *templates* se ven archivos *.jade* en lugar de plantillas *.html* y las vistas de *views.py* hacen referencia a estos archivos en sus llamadas a `flask.render_template`. En caso contrario, el código de las vistas es el mismo.

Si abre uno de los archivos *.jade*, puede ver la expresión más concisa de una plantilla. Por ejemplo, este es el contenido de *templates/layout.jade* tal como lo ha creado la plantilla "Proyecto web de Flask/Jade":

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

Y este es el contenido de *templates/about.jade*, donde se muestra el uso de `#{ <name>}` para los marcadores de posición:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

No dude en experimentar con la sintaxis de Jinja y de Jade para ver cuál le conviene más.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Plantilla de proyecto web de Flask de sondeos](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Escribir su primera aplicación de Flask, parte 4 (formas y vistas genéricas)](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade en GitHub (documentación)](https://github.com/liuliqiang/pyjade) (github.com)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
