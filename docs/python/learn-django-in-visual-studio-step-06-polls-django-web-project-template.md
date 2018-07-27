---
title: 'Tutorial: Información acerca de Django en Visual Studio, paso 6'
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio, en particular las características de la plantilla Proyecto web de Django de sondeos, como la personalización administrativa.
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
ms.openlocfilehash: d88f1e258bf8aa9801555c256f825841fff9d476
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089508"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Paso 6. Usar la plantilla de proyecto web de Django de sondeos

**Paso anterior: [Autenticación de los usuarios en Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Ahora que conoce la plantilla "Proyecto web de Django" de Visual Studio, podemos analizar la tercera plantilla de Django, "Proyecto web de Django de sondeos", que se basa en el mismo código base y demuestra el trabajo con una base de datos.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Crear un proyecto a partir de la plantilla e inicializar la base de datos (paso 6.1)
> - Comprender los modelos de datos (paso 6.2)
> - Aplicar migraciones (paso 6.3)
> - Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto (paso 6.4)
> - Crear una interfaz de administración personalizada (paso 6.5)

El proyecto creado con esta plantilla es similar al que se obtiene tras seguir el tutorial [Escribiendo su primera aplicación en Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) de la documentación de Django. La aplicación web consta de un sitio público que permite a los usuarios ver sondeos y votar en ellos, además de una interfaz de administración personalizada que sirve para administrar los sondeos. En ella se utiliza el mismo sistema de autenticación que en la plantilla "Proyecto web de Django" y se hace un mayor uso de la base de datos mediante la implementación de modelos de Django, tal y como se muestra en las secciones siguientes.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Paso 6.1: Crear el proyecto e inicializar la base de datos

1. En Visual Studio, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la solución "LearningDjango" que creó anteriormente en este tutorial y seleccione **Agregar** > **Nuevo proyecto**. (En caso de que desee utilizar una nueva solución, tendrá que seleccionar **Archivo** > **Nuevo** > **Proyecto**).

1. En el cuadro de diálogo del nuevo proyecto, busque y seleccione la plantilla "Proyecto web de Django de sondeos", asigne al proyecto el nombre "DjangoPolls" y seleccione **Aceptar**.

1. Al igual que otras plantillas de proyecto en Visual Studio, la plantilla "Proyecto web de Django de sondeos" incluye un archivo `requirements.txt`, y Visual Studio pregunta dónde instalar las dependencias. Elija la opción **Install into a virtual environment** (Instalar en un entorno virtual) y, en el cuadro de diálogo **Agregar entorno virtual**, seleccione **Crear** para aceptar los valores predeterminados.

1. Una vez que Python finalice la configuración del entorno virtual, siga las instrucciones del `readme.html` que aparece para inicializar la base de datos y crear un superusuario de Django (esto es, un administrador). Primero hay que hacer clic con el botón derecho en el proyecto "DjangoPolls" del **Explorador de soluciones** y seleccionar el comando **Python** > **Django Migrate** (Migrar Django); a continuación, haga clic con el botón derecho en el proyecto de nuevo, seleccione el comando **Python** > **Django Create Superuser** (Crear superusuario de Django) y siga las indicaciones. (Si intenta crear un superusuario primero, verá un error porque no se inicializó la base de datos).

1. Modifique la configuración para que el proyecto "DjangoPolls" sea el predeterminado para la solución de Visual Studio; para ello, haga clic con el botón derecho en ese proyecto en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**. El proyecto de inicio, que se muestra en negrita, es lo que ejecuta cuando se inicia el depurador.

1. Seleccione **Depurar > Iniciar depuración** (F5) o use el botón **Servidor web** de la barra de herramientas para ejecutar el servidor:

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/django/run-web-server-toolbar-button.png)

1. La aplicación creada por la plantilla tiene tres páginas: una de inicio, otra de información y otra de contacto, por las que puede navegar con la barra de la parte superior. Tómese un minuto o dos para examinar las diferentes partes de la aplicación (las páginas de información y contacto son muy similares al "Proyecto web de Django" y no se vuelven a tratar).

    ![Vista completa del explorador de la aplicación Proyecto web de Django de sondeos](media/django/step06-full-app-view.png)

1. Seleccione también el vínculo **Administración** en la barra de navegación, que muestra una pantalla de inicio de sesión para demostrar que la interfaz administrativa está autorizada únicamente para los administradores autenticados. Use las credenciales de superusuario y se le dirigirá a la página "/admin", que está habilitada de forma predeterminada cuando se usa esta plantilla de proyecto.

    ![Vista administrativa del explorador de la aplicación Proyecto web de Django de sondeos](media/django/step06-polls-administrative-interface.png)

1. Puede dejar la aplicación en ejecución para las secciones siguientes.

    Si desea detener la aplicación y [confirmar los cambios en el control de código fuente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), abra primero la página **Cambios** en **Team Explorer**, haga clic con el botón derecho en la carpeta del entorno virtual (probablemente `env`) y seleccione **Omitir estos elementos locales**.

### <a name="examine-the-project-contents"></a>Examen del contenido del proyecto

Como se indicó previamente, gran parte de lo que aparece en un proyecto creado a partir de la plantilla de "Proyecto web de Django de sondeos" debe resultarle familiar si ha explorado las otras plantillas de proyecto en Visual Studio. En el resto de pasos de este artículo se resumen los cambios y novedades más importantes; en especial, los modelos de datos y las vistas adicionales.

### <a name="question-what-does-the-django-migrate-command-do"></a>Pregunta: ¿Para qué sirve el comando Django Migrate (Migrar Django)?

Respuesta: El comando **Django Migrate** (Migrar Django) ejecuta específicamente el comando `manage.py migrate`, que ejecuta los scripts de la carpeta `app/migrations` que no se hayan ejecutado con anterioridad. En este caso, el comando ejecuta el script `0001_initial.py` en esa carpeta y configura el esquema necesario en la base de datos.

El propio script de migración se crea por el comando `manage.py makemigrations`, que examina el archivo `models.py` de la aplicación, lo compara con el estado actual de la base de datos y luego genera los scripts necesarios para migrar el esquema de la base de datos para que coincida con los modelos actuales. Esta característica de Django es muy eficaz, ya que permite actualizar y modificar los modelos a lo largo del tiempo. Mediante la generación y ejecución de migraciones, puede mantener los modelos y la base de datos sincronizados con bastante sencillez.

En el paso 6.3 de este artículo trabajará con una migración.

## <a name="step-6-2-understand-data-models"></a>Paso 6.2: Comprender los modelos de datos

Los modelos de la aplicación, llamados Poll y Choice, se definen en `app/models.py`. Cada uno de ellos es una clase de Python que se deriva de `django.db.models.Model` y usa los métodos de la clase `models`, como `CharField` y `IntegerField`, para definir campos en el modelo, que se asignan a columnas de la base de datos.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Como puede ver, un modelo Poll mantiene una descripción en su campo `text` y una fecha de publicación en `pub_date`. Estos campos son los únicos que existen para el elemento Poll de la base de datos. El campo `total_votes` se calcula en tiempo de ejecución.

Un elemento Choice se relaciona con un elemento Poll a través del campo `poll`, contiene una descripción en `text` y mantiene un recuento para esa opción en `votes`. El campo `votes_percentage` se calcula en tiempo de ejecución y no se encuentra en la base de datos.

La lista completa de tipos de campo es `CharField` (texto limitado), `TextField` (texto ilimitado), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` y `ManyToMany`. Cada campo tiene algunos atributos, como `max_length`. El atributo `blank=True` significa que el campo es opcional; `null=true` significa que un valor es opcional. También hay un atributo `choices` que limita los valores a valores en una matriz de tuplas de valor de datos/valor de visualización. (Consulte [Model field reference](https://docs.djangoproject.com/en/2.0/ref/models/fields/) [Modelado de referencia de campo] en la documentación de Django).

Puede confirmar exactamente qué está almacenado en la base de datos mediante el examen del archivo `db.sqlite3` en el proyecto con una herramienta como el [explorador SQLite](http://sqlitebrowser.org/). En la base de datos, verá que un campo de clave externa como `poll` en el modelo Choice se almacena como `poll_id`; Django controla la asignación automáticamente.

En general, trabajar con la base de datos en Django significa trabajar exclusivamente a través de los modelos para que Django pueda administrar la base de datos subyacente en su nombre.

### <a name="seed-the-database-from-samplesjson"></a>Inicialización de la base de datos a partir de samples.json

Inicialmente, la base de datos no contiene ningún sondeo. Puede usar la interfaz administrativa en la dirección URL "/admin" para agregar sondeos manualmente, y también puede visitar la página "/seed" en el sitio de ejecución para agregar el valor de inicialización de la base de datos con sondeos definidos en el archivo `samples.json` de la aplicación.

El `urls.py` del proyecto de Django tiene un patrón de dirección URL agregado: `url(r'^seed$', app.views.seed, name='seed'),`. La vista `seed` en `app/views.py` carga el archivo `samples.json` y crea los objetos de modelo necesarios. A continuación, Django crea automáticamente los registros coincidentes en la base de datos subyacente.

Observe el uso del decorador `@login_required` para indicar el nivel de autorización para la vista.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Para ver el efecto, ejecute la aplicación primero para ver que no existe todavía ningún sondeo. Luego, visite la dirección URL "/seed" y, cuando la aplicación vuelva a la página de inicio, debería constatar que los sondeos ya están disponibles. Una vez más, no dude en examinar el archivo `db.sqlite3` sin formato con una herramienta como el [explorador de SQLite](http://sqlitebrowser.org/).

![Aplicación Proyecto web de Django de sondeos con una base de datos inicializada](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Pregunta: ¿Es posible inicializar la base de datos con la utilidad administrativa de Django?

Respuesta: Sí, puede usar el [comando django-admin loaddata](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata) para realizar la misma tarea que la página de inicialización de la aplicación. Cuando se trabaja en una aplicación web completa, puede usar una combinación de los dos métodos: inicializar una base de datos desde la línea de comandos y, a continuación, convertir la página de inicialización aquí en una API a la que puede enviar cualquier otro JSON arbitrario en lugar de confiar en un archivo codificado de forma rígida.

## <a name="step-6-3-use-migrations"></a>Paso 6.3: Usar migraciones

Cuando ejecutó el comando `manage.py makemigrations` (mediante el menú contextual en Visual Studio) después de crear el proyecto, Django creó el archivo `app/migrations/0001_initial.py`. Este archivo contiene un script que crea las tablas de base de datos iniciales.

Habida cuenta que inevitablemente tendrá que hacer cambios en los modelos con el paso del tiempo, Django facilita la puesta al día del esquema de la base de datos subyacente con estos modelos. El flujo de trabajo general es el siguiente:

1. Haga cambios en los modelos en el archivo `models.py`.
1. En Visual Studio, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione el comando **Python** > **Django Make Migrations** (Hacer migraciones de Django). Tal y como se describió anteriormente, este comando genera scripts en `app/migrations` para migrar la base de datos de su estado actual al nuevo estado.
1. Para aplicar los scripts a la base de datos real, haga clic de nuevo en el proyecto con el botón derecho y seleccione **Python** > **Django Migrate** (Migrar Django).

Django realiza un seguimiento de las migraciones que se han aplicado a cualquier base de datos, de manera que cuando se ejecuta el comando de migración, Django aplica tantas migraciones como sean necesarias. Si crea una base de datos nueva y vacía, por ejemplo, la ejecución del comando de migración la pone al día con los modelos actuales aplicando cada script de migración. Del mismo modo, si realiza varios cambios en el modelo y genera las migraciones en un equipo de desarrollo, puede aplicar las migraciones acumulativas a la base de datos de producción con el comando de migración en el servidor de producción. Django de nuevo aplica solo aquellos scripts de migración que se han generado desde la última migración de la base de datos de producción.

Para ver el efecto del cambio de un modelo, pruebe lo siguiente:

1. Agregue un campo de autor opcional al modelo Poll en `app/models.py` agregando la siguiente línea después del campo `pub_date` para agregar un campo `author` opcional:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Guarde el archivo, haga clic con el botón derecho en el proyecto "DjangoPolls" en el **Explorador de soluciones** y seleccione el comando **Python** > **Django Make Migrations** (Hacer migraciones de Django).
1. Seleccione **Proyecto** > **Mostrar todos los archivos** para ver el script recién generado en la carpeta `migrations`, cuyo nombre empieza por `002_auto_`. Haga clic con el botón derecho en ese archivo y seleccione **Incluir en el proyecto**. A continuación, puede seleccionar **Proyecto** > **Mostrar todos los archivos** de nuevo para restaurar la vista original. (Vea la segunda pregunta a continuación para obtener más información acerca de este paso).
1. Si lo desea, abra el archivo para examinar la manera en que Django refleja en script el cambio del estado del modelo anterior al nuevo estado.
1. Haga clic de nuevo en el proyecto de Visual Studio con el botón derecho y seleccione **Python** > **Django Migrate** (Migrar Django) para aplicar los cambios a la base de datos.
1. Si lo desea, abra la base de datos en un visor adecuado para confirmar el cambio.

En general, la característica de migración de Django implica que no tendrá que administrar nunca el esquema de base de datos manualmente. Simplemente realice cambios en los modelos, genere los scripts de migración y aplíquelos con el comando de migración.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Pregunta: ¿Qué sucede si olvido ejecutar el comando de migración después de realizar cambios en los modelos?

Respuesta: Si los modelos no coinciden con lo que aparece en la base de datos, Django genera un error en tiempo de ejecución con las excepciones apropiadas. Por ejemplo, si se olvida de migrar el cambio de modelo que se muestra en la sección anterior, verá el error "no such column: app_poll.author":

![error que se muestra cuando no se ha migrado un cambio de modelo](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Pregunta: ¿Por qué el Explorador de soluciones no muestra los scripts recién generados después de ejecutar Django Make Migrations (Hacer migraciones de Django)?

Respuesta: Aunque los scripts recién generados existen en la carpeta `app/migrations` y se aplican cuando se ejecuta el comando **Django Migrate** (Migrar Django), no aparecen automáticamente en el **Explorador de soluciones** porque no se han agregado al proyecto de Visual Studio. Para que sean visibles, seleccione primero el comando de menú **Proyecto** > **Mostrar todos los archivos** o el botón de la barra de herramientas que se describe en la siguiente imagen. Este comando hace que el **Explorador de soluciones** muestre todos los archivos en la carpeta del proyecto, con un icono de contorno punteado para los elementos que no se han agregado al propio proyecto. Haga clic con el botón derecho en los archivos que desea agregar y seleccione **Incluir en el proyecto**, lo cual los incluye también en el control de código fuente en la siguiente confirmación.

![Comando Incluir en el proyecto en el Explorador de soluciones](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Pregunta: ¿Puedo ver qué migraciones se aplicarían antes de ejecutar el comando de migración?

Respuesta: Sí, use el [comando django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Paso 6.4: Comprender las vistas y las plantillas de página creadas por la plantilla de proyecto

La mayoría de las vistas generadas por la plantilla "Proyecto web de Django de sondeos", como las vistas de las páginas de información y contacto, son muy similares a las vistas creadas por la plantilla "Proyecto web de Django" con la que trabajó anteriormente en este tutorial. La diferencia en la aplicación Polls es que su página principal utiliza los modelos, como hacen otras páginas añadidas para votar y ver los resultados de los sondeos.

Para comenzar, la primera línea de la matriz `urlpatterns` del proyecto Django en el archivo `urls.py` es más que un simple enrutamiento a una vista de la aplicación. Lo que hace es incorporar el propio archivo `urls.py` de la aplicación:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Así pues, el archivo `app/urls.py` contiene código de enrutamiento más interesante (se incluye una explicación):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Si no está familiarizado con las expresiones regulares más complejas que se usan aquí, puede pegar la expresión en [regex101.com](https://regex101.com/) para obtener una explicación en un lenguaje claro. (Necesitará convertir en escape las barras diagonales `/` mediante la adición de una barra diagonal inversa `\` delante; el escape no es necesario en Python por el prefijo `r` de la cadena, que significa "raw" [sin formato]).

En Django, la sintaxis `?P<name>pattern` crea un grupo denominado `name`, que se pasa como argumentos a vistas en el orden en que aparecen. En el código mostrado anteriormente, `PollsDetailView` y `PollsResultsView` reciben un argumento con nombre `pk` y `app.views.vote` recibe un argumento denominado `poll_id`.

También puede ver que la mayoría de las vistas no son simplemente referencias directas a una función de vista en `app/views.py`. En su lugar, la mayoría hacen referencia a una clase de ese mismo archivo que se deriva de `django.views.generic.ListView` o `django.views.generic.DetailView`. Las clases base proporcionan los métodos `as_view`, que tienen un argumento `template_name` para identificar la plantilla. La clase base `ListView`, como se usa para la página principal, también espera una propiedad `queryset` que contiene los datos y una propiedad `context_object_name` con el nombre de la variable por la que desea hacer referencia a los datos en la plantilla; en este caso, `latest_poll_list`.

Ahora puede examinar `PollListView` para la página principal, que se define como se indica a continuación en `app/views.py`:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Todo lo que se hace aquí sirve para identificar el modelo con el que funciona la vista (Poll) y reemplazar el método `get_context_data` para agregar los valores `title` y `year` al contexto.

Básicamente, la plantilla (`templates/app/index.html`) es así:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

En pocas palabras, la plantilla recibe la lista de objetos de Polls en `latest_poll_list` y, a continuación, recorre en iteración la lista para crear una fila de tabla que contiene un vínculo a cada sondeo por medio del valor `text` del sondeo. En la etiqueta `{% url %}`, "app:detail" hace referencia al patrón de dirección URL de `app/urls.py` denominado "detail", con `poll.id` como argumento. El efecto es que Django crea una dirección URL con el patrón adecuado y lo utiliza para el vínculo. Esta pequeña prueba de futuro significa que puede cambiar ese patrón de dirección URL en cualquier momento, y los vínculos generados se actualizan automáticamente para coincidir.

Las clases `PollDetailView` y `PollResultsView` de `app/views.py` (que no se muestran aquí) son casi idénticas a `PollListView`, a excepción de que se derivan de `DetailView`. Las plantillas correspondientes, `app/templates/details.html` y `app/templates/results.html`, colocan entonces los campos adecuados desde los modelos en diferentes controles HTML. Una parte única de `details.html` es que las opciones de un sondeo están contenidas dentro de un formulario HTML que, cuando se envía, realiza un POST a la dirección URL /vote. Como se ha visto antes, este patrón de dirección URL se enruta a `app.views.vote`, que se implementa como sigue (observe el argumento `poll_id`, que es de nuevo un grupo con nombre en la expresión regular utilizada en el enrutamiento para esta vista):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

En este caso, la vista no tiene su propia plantilla correspondiente, como las otras páginas. En su lugar, valida el sondeo seleccionado, que muestra un error 404 si el sondeo no existe (solo en caso de que alguien escriba una dirección URL como "vote/1a2b3c"). Luego se asegura de que la opción votada sea válida para el sondeo. Si no es así, el bloque `except` simplemente representa la página de detalles de nuevo con un mensaje de error. Si la opción es válida, la vista registra el voto y lo redirecciona a la página de resultados.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Paso 6.5: Crear una interfaz de administración personalizada

Los últimos datos de la plantilla de "Proyecto web de Django de sondeos" son las extensiones personalizadas para la interfaz administrativa de Django personalizada, tal como se mostró anteriormente en el paso 6.1 de este artículo. La interfaz predeterminada ofrece administración de usuario y grupo, pero nada más. La plantilla de proyecto de sondeos agrega características que le permiten también administrar los sondeos.

En primer lugar, los patrones de la dirección URL en `urls.py` del proyecto Django tiene `url(r'^admin/', include(admin.site.urls)),` incluido de manera predeterminada; el patrón "admin/doc" está incluido también mediante la conversión en comentario.

La aplicación entonces contiene el archivo `admin.py`, que Django ejecuta automáticamente al visitar la interfaz administrativa gracias a la inclusión de `django.contrib.admin` en la matriz `INSTALLED_APPS` de `settings.py`. El código en ese archivo, tal y como se especifica en la plantilla del proyecto, es el siguiente:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Como puede ver, la clase `PollAdmin` se deriva de `django.contrib.admin.ModelAdmin` y personaliza un número de sus campos con nombres del modelo `Poll`, que administra. Estos campos se describen en las opciones de [ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) en la documentación de Django.

La llamada a `admin.site.register` conecta entonces esa clase al modelo (`Poll`) y lo incluye en la interfaz de administración. El resultado global se muestra a continuación:

![Vista administrativa del explorador de la aplicación Proyecto web de Django de sondeos](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Pasos siguientes

> [!Note]
> Si ha estado confirmando la solución de Visual Studio en el control de código fuente en el transcurso de este tutorial, ahora es un buen momento de hacer otra confirmación. La solución debe coincidir con el código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Ya ha explorado por completo las plantillas "Proyecto web de Django en blanco", "Proyecto web de Django" y "Proyecto web de Django de sondeos" en Visual Studio. Ha aprendido todos los elementos básicos de Django, como el uso de vistas y plantillas, y ha explorado el enrutamiento, la autenticación y el uso de modelos de base de datos. Ahora podrá crear una aplicación web propia con las vistas y los modelos que necesite.

La ejecución de una aplicación web en el equipo de desarrollo es solamente un paso en el proceso de poner la aplicación a disposición de sus clientes. Los pasos siguientes pueden incluir las siguientes tareas:

- Implementar la aplicación web en un servidor de producción, como Azure App Service. Vea [Publish to Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) (Publicación en Azure App Service), que incluye los cambios específicos necesarios para las aplicaciones de Django.

- Personalizar la página 404 mediante la creación de una plantilla denominada `templates/404.html`. Cuando está presente, Django utiliza esta plantilla en lugar de la predeterminada. Para obtener más información, consulte [Error views](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) (Vistas de error) en la documentación de Django.

- Escribir pruebas unitarias en `tests.py`; las plantillas de proyecto de Visual Studio proporcionan puntos de inicio para estas, y puede encontrar más información en [Escribiendo su primera aplicación en Django, parte 5 - Pruebas](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) y [Testing in Django](https://docs.djangoproject.com/en/2.0/topics/testing/) (Pruebas en Django) en la documentación de Django.

- Cambiar la aplicación de SQLite a un almacén de datos a nivel de producción como PostgreSQL, MySQL y SQL Server (todos se pueden hospedar en Azure). Como se describe en [When to use SQLite](https://www.sqlite.org/whentouse.html) (Cuándo usar SQLite) (sqlite.org), SQLite funciona perfectamente en sitios de tráfico bajo a medio, con menos de 100.000 visitas al día, pero no se recomienda en volúmenes más elevados. También está limitado a un único equipo, por lo tanto no se puede usar en escenarios de varios servidores, como el equilibrio de carga y la replicación geográfica. Para obtener información sobre la compatibilidad con Django otras bases de datos, vea [Configuración de la base de datos](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). También puede usar el [SDK de Azure para Python](azure-sdk-for-python.md) para trabajar con los servicios de almacenamiento de Azure, como tablas y blobs.

- Configurar una canalización de implementación continua/integración continua en un servicio como Visual Studio Team Services (VSTS). Además de funcionar con el control de código fuente (en VSTS, GitHub u otro servicio), puede hacer que VSTS ejecute automáticamente pruebas unitarias como requisito previo para la publicación, y también configurar la canalización para implementar en un servidor de ensayo para pruebas adicionales antes de implementar en producción. VSTS, además, se integra con soluciones de supervisión como App Insights y cierra todo el ciclo con herramientas de planeación de agile. Para obtener más información, consulte:

  - [Create a CI/CD pipeline for Python with the Azure DevOps project](/vsts/build-release/apps/cd/azure/azure-devops-project-python?view=vsts) (Creación de una canalización de implementación continua/integración continua con el proyecto DevOps de Azure)
  - [Python development in Azure with Visual Studio Team Services (video, 11m 21s)](https://azure.microsoft.com/resources/videos/connect-2017-python-development-in-azure-with-visual-studio-team-services/). (Desarrollo de Python en Azure con Visual Studio Team Services [vídeo, 11m 21s])

