---
title: Información sobre el paso 5 del tutorial de Django en Visual Studio, Autenticación
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio, en particular las características de autenticación proporcionadas por las plantillas Proyecto web de Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f589aed953a852cb57570988d914f77b2fa10b2
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806022"
---
# <a name="step-5-authenticate-users-in-django"></a>Paso 5: Autenticación de usuarios en Django

**Paso anterior: [Uso de la plantilla completa de Proyecto web de Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
Dado que la autenticación es una necesidad común para las aplicaciones web, la plantilla "Proyecto web de Django" incluye un flujo de autenticación básica. (La plantilla "Proyecto web de Django de sondeos", que se describe en el paso 6 de este tutorial, también incluye el mismo flujo). Al usar cualquiera de las plantillas de proyecto de Django, Visual Studio incluye todos los módulos necesarios para la autenticación en el archivo *settings.py* del proyecto de Django.
::: moniker-end

::: moniker range=">=vs-2019"
Dado que la autenticación es una necesidad común para las aplicaciones web, la plantilla "Proyecto web de Django" incluye un flujo de autenticación básica. Al usar cualquiera de las plantillas de proyecto de Django, Visual Studio incluye todos los módulos necesarios para la autenticación en el archivo *settings.py* del proyecto de Django.
::: moniker-end

En este paso, aprenderá lo siguiente:

> [!div class="checklist"]
> - Cómo usar el flujo de autenticación proporcionado en las plantillas de Visual Studio (paso 5.1)

## <a name="step-5-1-use-the-authentication-flow"></a>Paso 5-1: Uso del flujo de autenticación

En los pasos siguientes se utiliza el flujo de autenticación y se describen las partes del proyecto que intervienen:

1. Si no ha seguido todavía las instrucciones del archivo *readme.html* de la raíz del proyecto para crear una cuenta de superusuario (administrador), hágalo ahora.

1. Ejecute la aplicación desde Visual Studio mediante **Depurar** > **Iniciar depuración** (**F5**). Cuando la aplicación aparezca en el explorador, observe que aparece **Iniciar sesión** en la esquina superior derecha de la barra de navegación.

    ![Control de inicio de sesión en la página de aplicación del Proyecto web de Django](media/django/step05-login-control.png)

1. Abra *templates/app/layout.html* y observe que el elemento `<div class="navbar ...>` contiene la etiqueta `{% include app/loginpartial.html %}`. La etiqueta `{% include %}` indica al sistema de plantillas de Django que incorpore el contenido del archivo incluido en este momento en la plantilla que lo contiene.

1. Abra *templates/app/loginpartial.html* y observe cómo usa la etiqueta condicional `{% if user.is_authenticated %}` junto con una etiqueta `{% else %}` para representar diferentes elementos de la interfaz de usuario en función de si se ha autenticado al usuario:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Habida cuenta que no hay ningún usuario autenticado al iniciar la aplicación por primera vez, este código de plantilla representa solo el vínculo "Iniciar sesión" en la ruta de acceso relativa "login". Como se especifica en *urls.py* (tal como se muestra en la sección anterior), esa ruta está asignada a la vista `django.contrib.auth.views.login`. Esa vista recibe los siguientes datos:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Aquí, `template_name` identifica la plantilla de la página de inicio de sesión, en este caso *templates/app/login.html*. La propiedad `extra_context` se agrega a los datos de contexto predeterminados proporcionados a la plantilla. Por último, `authentication_form` especifica una clase de formulario que se usa con el inicio de sesión; en la plantilla aparece como objeto `form`. El valor predeterminado es `AuthenticationForm` (de `django.contrib.auth.views`); la plantilla de proyecto de Visual Studio usa en su lugar el formulario definido en el archivo *forms.py* de la aplicación:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Como puede ver, esta clase de formulario se deriva de `AuthenticationForm` e invalida específicamente los campos de nombre de usuario y contraseña para agregar texto de marcador de posición. La plantilla de Visual Studio incluye este código explícito suponiendo que probablemente quiera personalizar el formulario, por ejemplo, agregando una característica de validación de la seguridad de la contraseña.

1. Cuando se desplaza a la página de inicio de sesión, la aplicación representa la plantilla *login.html*. Las variables `{{ form.username }}` y `{{ form.password }}` representan los formularios `CharField` de `BootstrapAuthenticationForm`. También hay una sección integrada para mostrar errores de validación, y un elemento listo para su uso para los inicios de sesión con medios sociales, por si opta por agregar esos servicios.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Cuando se envía el formulario, Django intenta autenticar las credenciales (por ejemplo, las credenciales del superusuario). Si se produce un error en la autenticación, permanecerá en la página actual, pero `form.errors` se establecerá en true. Si la autenticación se realiza correctamente, Django navegará a la dirección URL relativa del campo "next", `<input type="hidden" name="next" value="/" />`, que en este caso es la página principal (`/`).

1. Ahora, cuando se vuelve a representar la página principal, la propiedad `user.is_authenticated` es true si se representa la plantilla *loginpartial.html*. Como resultado, se ve un mensaje **Hello (nombre de usuario)** y **Cerrar sesión**. Puede usar `user.is_authenticated` en otras partes de la aplicación para comprobar la autenticación.

    ![Mensaje Hello y control de cierre de sesión en la página de la aplicación del Proyecto web de Django](media/django/step05-logoff-control.png)

1. Para comprobar si el usuario autenticado está autorizado a acceder a recursos específicos, deberá recuperar permisos específicos de usuario de la base de datos. Para obtener más información, vea [Using the Django authentication system](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Uso del sistema de autenticación de Django) (Documentación de Django).

1. El superusuario o el administrador, en concreto, está autorizado a acceder a las interfaces de administrador de Django integradas con las direcciones URL relativas "/admin/" y "/admin/doc/". Para habilitar estas interfaces, haga lo siguiente:

    1. Instale el paquete de Python docutils en el entorno. Una excelente manera de hacerlo es agregar "docutils" al archivo *requirements.txt* y, luego, en el **Explorador de soluciones**, expandir el nodo **Entornos de Python**, hacer clic con el botón derecho en el entorno que está usando y seleccionar **Instalar desde requirements.txt**.

    1. Abra el archivo *urls.py* del proyecto de Django y quite los comentarios predeterminados de las siguientes entradas:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. En el archivo *settings.py* del proyecto de Django, vaya a la colección `INSTALLED_APPS` y agregue `'django.contrib.admindocs'`.

    1. Cuando reinicie la aplicación, puede ir a "/admin/" y "/admin/doc/" y realizar tareas como crear cuentas de usuario adicionales.

        ![Interfaz del administrador de Django](media/django/step05-administrator-interface.png)

1. La parte final del flujo de autenticación es el cierre de sesión. Como puede ver en *loginpartial.html*, el vínculo **Cerrar sesión** simplemente realiza una operación POST a la dirección URL relativa "/login", que se controla mediante la vista integrada `django.contrib.auth.views.logout`. Esta vista no muestra ninguna interfaz de usuario y solo se desplaza a la página principal (como se muestra en *urls.py* para el patrón "^logout$"). Si desea mostrar una página de cierre de sesión, cambie primero el patrón de dirección URL como se indica a continuación para agregar una propiedad "template_name" y quite la propiedad "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Luego cree *templates/app/loggedoff.html* con el siguiente contenido (mínimo):

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    El resultado se muestra de la manera siguiente:

    ![Página de cierre de sesión agregada](media/django/step05-logged-off-page.png)

1. Cuando haya terminado, detenga el servidor y una vez más confirme los cambios en el control de código fuente.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cuál es la finalidad de la etiqueta {% csrf_token %} que aparece en los elementos \<form\>?

Respuesta: La etiqueta `{% csrf_token %}` incluye la [protección de falsificación de solicitud entre sitios (csrf)](https://docs.djangoproject.com/en/2.0/ref/csrf/) integrada de Django (documentación de Django). Normalmente se agrega esta etiqueta a cualquier elemento que incluya los métodos de solicitud POST, PUT o DELETE, como un formulario. Luego, la función de representación de la plantilla (`render`) inserta la protección necesaria.

## <a name="next-steps"></a>Pasos siguientes

::: moniker range="vs-2017"
- [Usar la plantilla de proyecto web de Django de sondeos](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Si ha estado confirmando la solución de Visual Studio en el control de código fuente en el transcurso de este tutorial, ahora es un buen momento de hacer otra confirmación. La solución debe coincidir con el código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Ya ha explorado por completo las plantillas "Proyecto web de Django en blanco" y "Proyecto web de Django" en Visual Studio. Ha aprendido todos los elementos básicos de Django, como el uso de vistas y plantillas, y ha explorado el enrutamiento, la autenticación y el uso de modelos de base de datos. Ahora podrá crear una aplicación web propia con las vistas y los modelos que necesite.

La ejecución de una aplicación web en el equipo de desarrollo es solamente un paso en el proceso de poner la aplicación a disposición de sus clientes. Los pasos siguientes pueden incluir las siguientes tareas:

- Implementar la aplicación web en un servidor de producción, como Azure App Service. Consulte [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Personalice la página 404 mediante la creación de una plantilla denominada *templates/404.html*. Cuando está presente, Django utiliza esta plantilla en lugar de la predeterminada. Para obtener más información, consulte [Error views](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) (Vistas de error) en la documentación de Django.

- Escriba pruebas unitarias en *tests.py*; las plantillas de proyecto de Visual Studio proporcionan puntos de inicio para eso; además, puede encontrar más información en [Writing your first Django app, part 5 - testing](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) (Escribir la primera aplicación de Django, parte 5: pruebas) y [Testing in Django](https://docs.djangoproject.com/en/2.0/topics/testing/) (Pruebas en Django) en la documentación de Django.

- Cambiar la aplicación de SQLite a un almacén de datos a nivel de producción como PostgreSQL, MySQL y SQL Server (todos se pueden hospedar en Azure). Como se describe en [When to use SQLite](https://www.sqlite.org/whentouse.html) (Cuándo usar SQLite) (sqlite.org), SQLite funciona perfectamente en sitios de tráfico bajo a medio, con menos de 100.000 visitas al día, pero no se recomienda en volúmenes más elevados. También está limitado a un único equipo, por lo tanto no se puede usar en escenarios de varios servidores, como el equilibrio de carga y la replicación geográfica. Para obtener información sobre la compatibilidad con Django otras bases de datos, vea [Configuración de la base de datos](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). También puede usar el [SDK de Azure para Python](/azure/python/) para trabajar con los servicios de almacenamiento de Azure, como tablas y blobs.

- Configurar una canalización de implementación continua/integración continua en un servicio como Azure DevOps. Además de funcionar con el control de código fuente (en Azure Repos, GitHub u otro servicio), puede configurar un proyecto de Azure DevOps para que ejecute automáticamente pruebas unitarias como requisito previo para la publicación y también configurar la canalización para implementar en un servidor de ensayo para pruebas adicionales antes de implementar en producción. Azure DevOps, además, se integra con soluciones de supervisión como App Insights y cierra todo el ciclo con herramientas de planeación de Ágil. Para obtener más información, consulte [Creación de una canalización de CI/CD para Python con Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) y también la [Azure DevOps Documentation](/azure/devops/?view=vsts&preserve-view=true) (Documentación de Azure DevOps) general.
::: moniker-end
## <a name="go-deeper"></a>Profundizar un poco más

- [User authentication in Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (Autenticación de usuarios en Django) (docs.djangoproject.com)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
