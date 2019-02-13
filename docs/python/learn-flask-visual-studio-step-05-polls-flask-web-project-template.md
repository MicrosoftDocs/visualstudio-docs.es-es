---
title: Información sobre el paso 5 del tutorial de Flask en Visual Studio, Plantilla de proyecto de sondeos
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Flask en el contexto de los proyectos de Visual Studio, en particular las características de las plantillas Proyecto web de Flask de sondeos y Proyecto web de Flask/Jade de sondeos.
ms.date: 01/07/2019
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 38b77b4461303cd4bf21b98c63c1ae0b93a4cdc6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913397"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Paso 5: Uso de la plantilla de proyecto web de sondeos de Flask

**Paso anterior: [Uso de la plantilla de proyecto web completa de Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Ahora que conoce la plantilla "Proyecto web de Flask" de Visual Studio, podemos analizar la tercera plantilla de Flask, "Proyecto web de Flask de sondeos", que se basa en el mismo código base.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Crear un proyecto a partir de la plantilla e inicializar la base de datos (paso 5-1)
> - Comprender los modelos de datos (paso 5-2)
> - Comprender los almacenes de datos de copia de seguridad (paso 5-3)
> - Comprender los detalles de los sondeos y las vistas de resultados (paso 5-4)

Visual Studio también proporciona la plantilla "Proyecto web de Flask/Jade de sondeos", que genera una aplicación idéntica, pero usa la extensión de Jade para el motor de plantillas de Jinja. Para obtener información detallada, vea [Paso 4: Plantilla de proyecto web de Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Paso 5-1: Crear el proyecto

1. En Visual Studio, vaya al **Explorador de soluciones**, haga clic con el botón derecho en la solución **LearningFlask** creada anteriormente en este tutorial y seleccione **Agregar** > **Nuevo proyecto**. (En caso de que desee utilizar una nueva solución, tendrá que seleccionar **Archivo** > **Nuevo** > **Proyecto**).

1. En el cuadro de diálogo del nuevo proyecto, busque y seleccione la plantilla **Proyecto web de Flask de sondeos**, asigne al proyecto el nombre "FlaskPolls" y haga clic en **Aceptar**.

1. Al igual que otras plantillas de proyecto de Visual Studio, la plantilla "Proyecto web de Flask de sondeos" incluye un archivo *requirements.txt*, y Visual Studio pregunta dónde instalar esas dependencias. Elija la opción **Install into a virtual environment** (Instalar en un entorno virtual) y, en el cuadro de diálogo **Agregar entorno virtual**, seleccione **Crear** para aceptar los valores predeterminados. Esta plantilla requiere Flask, además de los paquetes azure-storage y pymongo. La plantilla "Proyecto web de Flask/Jade de sondeos" también requiere pyjade.

1. Establezca el proyecto **FlaskPolls** como predeterminado para la solución de Visual Studio. Para ello, haga clic con el botón derecho en ese proyecto en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**. El proyecto de inicio, que se muestra en negrita, es lo que ejecuta cuando se inicia el depurador.

1. Seleccione **Depurar** > **Iniciar depuración** (**F5**) o use el botón **Servidor web** de la barra de herramientas para ejecutar el servidor:

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/django/run-web-server-toolbar-button.png)

1. La aplicación creada por la plantilla tiene tres páginas: una de inicio, otra de información y otra de contacto, por las que puede navegar con la barra de la parte superior. Tómese un minuto o dos para examinar las diferentes partes de la aplicación (las páginas de información y contacto son muy similares al "Proyecto web de Flask" y no se vuelven a tratar).

    ![Vista completa de la aplicación Proyecto web de Flask de sondeos](media/flask/step06-full-app-view.png)

1. En la página principal, con el botón **Create Sample Polls** (Crear sondeos de ejemplo) se inicializa el almacén de datos de la aplicación con tres sondeos diferentes que se describen en la página *models/samples.json*. De forma predeterminada, la aplicación usa una base de datos en memoria (como se muestra en la página Acerca de), que se restablece cada vez que se reinicia la aplicación. La aplicación también contiene código para que funcione con Azure Storage y MongoDB, como se describe más adelante en este artículo.

1. Una vez que haya inicializado el almacén de datos, puede votar en los distintos sondeos, tal y como se muestra en la página principal (la barra de navegación y el pie de página se omiten por razones de brevedad):

    ![Vista de la aplicación de sondeos una vez inicializado el almacén de datos](media/flask/step06-polls-initialized.png)

1. Al seleccionar un sondeo se muestran las distintas opciones:

    ![Interfaz de voto de un sondeo](media/flask/step06-polls-voting-interface.png)

1. Una vez que haya votado, la aplicación mostrará una página de resultados y le permitirá volver a votar:

    ![Vista de resultados después de la votación](media/flask/step06-polls-results.png)

1. Puede dejar la aplicación en ejecución para las secciones siguientes.

    Si quiere detener la aplicación y [confirmar los cambios en el control de código fuente](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), primero abra la página **Cambios** en **Team Explorer**, haga clic con el botón derecho en la carpeta del entorno virtual (probablemente **env**) y seleccione **Omitir estos elementos locales**.

### <a name="examine-the-project-contents"></a>Examen del contenido del proyecto

Como se indicó previamente, gran parte de lo que aparece en un proyecto creado a partir de la plantilla "Proyecto web de Flask de sondeos" (y de la plantilla "Proyecto web de Flask/Jade de sondeos") debería resultarle familiar si ha explorado las otras plantillas de proyecto de Visual Studio. En el resto de pasos de este artículo se resumen los cambios y novedades más importantes; en especial, los modelos de datos y las vistas adicionales.

## <a name="step-5-2-understand-the-data-models"></a>Paso 5-2: Comprender los modelos de datos

Los modelos de datos de la aplicación son clases de Python denominadas Poll y Choice, que se definen en *models/\_\_init\_\_.py*. La clase Poll (Sondeo) representa una pregunta, para la que una colección de instancias Choice (Opción) representan las respuestas disponibles. Una clase Poll también mantiene el número total de votos (de cualquier opción) y un método para calcular las estadísticas que se usan para generar las vistas:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Estos modelos de datos son abstracciones genéricas con las que pueden funcionar las vistas de la aplicación en distintos tipos de almacenes de datos de copia de seguridad, que se describen en el siguiente paso.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Paso 5-3: Comprender los almacenes de datos de respaldo

La aplicación creada por la plantilla "Proyecto web de Flask de sondeos" se puede ejecutar en un almacén de datos en memoria, en un almacenamiento de tablas de Azure o en una base de datos de MongoDB.

El mecanismo de almacenamiento de datos funciona del siguiente modo:

1. El tipo de repositorio se especifica mediante la variable de entorno `REPOSITORY_NAME`, que se puede establecer en "memory", "azuretablestore" o "mongodb". Una sección de código de *settings.py* recupera el nombre con "memory" como valor predeterminado. Si quiere cambiar la memoria auxiliar, tendrá que establecer la variable de entorno y reiniciar la aplicación.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Luego, el código de *settings.py* inicializa un objeto `REPOSITORY_SETTINGS`. Si quiere usar el almacenamiento de tablas de Azure o MongoDB, primero deberá inicializar estos almacenes de datos en otro lugar y luego deberá establecer las variables de entorno necesarias que indiquen a la aplicación cómo debe conectarse al almacén:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. En *views.py*, la aplicación llama a Factory Method para inicializar un objeto `Repository` mediante el nombre y la configuración del almacén de datos:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. El método `factory.create_repository` está en *models\factory.py*, que simplemente importa el módulo de repositorio adecuado y luego crea una instancia `Repository`:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Las implementaciones de la clase `Repository` que son específicas de cada almacén de datos pueden encontrarse en *models\azuretablestorage.py*, *models\mongodb.py* y *models\memory.py*. La implementación de Azure Storage usa el paquete azure-storage, mientras que la implementación de MongoDB usa el paquete pymongo. Como se ha indicado en el paso 5-1, ambos paquetes se incluyen en el archivo *requirements.txt* de la plantilla del proyecto. La exploración de los detalles se deja como un ejercicio para el lector.

En resumen, la clase `Repository` sintetiza los detalles del almacén de datos y la aplicación usa variables de entorno en tiempo de ejecución para seleccionar y configurar cuál de las tres implementaciones se va a emplear.

En los siguientes pasos se incorpora compatibilidad para un almacén de datos diferente de los tres que se proporcionan en la plantilla del proyecto, si así se desea:

1. Copie *memory.py* en un archivo nuevo para disponer de la interfaz básica para la clase `Repository`.
1. Modifique la implementación de la clase para que se adapte al almacén de datos que está usando.
1. Modifique *factory.py* para agregar otro caso `elif` que reconozca el nombre del almacén de datos agregado e importe el módulo adecuado.
1. Modifique *settings.py* para reconocer otro nombre de la variable de entorno `REPOSITORY_NAME` y para inicializar `REPOSITORY_SETTINGS` en consecuencia.

### <a name="seed-the-data-store-from-samplesjson"></a>Inicializar el almacén de datos desde samples.json

En principio, ninguno de los almacenes de datos elegidos contiene sondeos, por lo que en la página principal de la aplicación se muestra el mensaje **No polls available** (No hay ningún sondeo disponible) junto con el botón **Create Sample Polls** (Crear sondeos de ejemplo). Pero, una vez que haya hecho clic en el botón, la vista cambiará para mostrar los sondeos disponibles. Este cambio se produce mediante etiquetas condicionales de *templates\index.html* (se han omitido algunas líneas en blanco por razones de brevedad):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

La variable `polls` de la plantilla procede de una llamada a `repository.get_polls`, que no devuelve nada hasta que se inicializa el almacén de datos.

Al hacer clic en el botón **Create Sample Polls** (Crear sondeos de ejemplo), se le redirigirá a la dirección URL /seed. El controlador de esa ruta se define en *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

La llamada a `repository.add_sample_polls()` termina en una de las implementaciones `Repository` específicas del almacén de datos elegido. Cada implementación llama al método `_load_samples_json` que se encuentra en *models\_\_init\_\_.py* para cargar el archivo *models\samples.json* en la memoria. Luego, recorre en iteración esos datos para crear los objetos `Poll` y `Choice` necesarios en el almacén de datos.

Una vez concluido dicho proceso, la instrucción `redirect('/')` del método `seed` vuelve a la página principal. Dado que `repository.get_polls` ahora devuelve un objeto de datos, las etiquetas condicionales de *templates\index.html* ahora representan una tabla que contiene los sondeos.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cómo se agregan sondeos nuevos a la aplicación?

Respuesta: La aplicación, tal y como se proporciona mediante la plantilla de proyecto, no incluye ninguna herramienta para agregar o editar sondeos. Puede modificar *models\samples.json* para crear nuevos datos de inicialización, pero eso implicaría el restablecimiento del almacén de datos. Para implementar características de edición, deberá ampliar la interfaz de la clase `Repository` con métodos para crear las instancias `Choice` y `Poll` necesarias. Luego, deberá implementar una interfaz de usuario en más páginas que usen estos métodos.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Paso 5-4: Comprender los detalles de los sondeos y las vistas de resultados

La mayoría de las vistas generadas por las plantillas "Proyecto web de Flask de sondeos" y "Proyecto web de Flask/Jade de sondeos", como las vistas de las páginas Acerca de y Contacto, son muy similares a las vistas creadas por la plantilla "Proyecto web de Flask" (o "Proyecto web de Flask/Jade") con la que ha trabajado en este tutorial. En la sección anterior también ha aprendido cómo se implementa la página principal para que se muestre el botón de inicialización o la lista de sondeos.

Lo que queda es examinar los votos (detalles) y la vista de resultados de un sondeo concreto.

Al seleccionar un sondeo de la página principal, la aplicación va a la dirección URL /poll/\<clave\>, donde *clave* es el identificador único de un sondeo. En *views.py*, puede ver que se asigna la función `details` para controlar ese enrutamiento de dirección URL para GET y las solicitudes. También puede observar que, al usar `<key>` en el enrutamiento de dirección URL, se asigna cualquier ruta que tenga ese formato a la misma función y se genera un argumento a la función con ese mismo nombre:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Para mostrar un sondeo (solicitudes GET), esta función simplemente llama a *templates\details.html*, que recorre en iteración la matriz `choices` del sondeo y crea un botón de radio para cada uno.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Dado que el botón **Votar** tiene `type="submit"`, al hacer clic en él se genera una solicitud POST que vuelve a la misma dirección URL que se enruta una vez más a la función `details`. Pero esta vez extrae la opción de los datos del formulario y se redirige a /results/\<opción\>.

La dirección URL results/\<key\> se enruta a la función `results` de *views.py*, que luego llama al método `calculate_stats` del sondeo y emplea *templates\results.html* para la representación:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

La plantilla *results.html*, por su parte, recorre en iteración las opciones del sondeo y genera una barra de progreso para cada una:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Pasos siguientes

> [!Note]
> Si ha estado confirmando la solución de Visual Studio en el control de código fuente en el transcurso de este tutorial, ahora es un buen momento de hacer otra confirmación. La solución debe coincidir con el código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Ya ha explorado por completo las plantillas "Proyecto web de Flask en blanco", "Proyecto web de Flask[/Jade]" y "Proyecto web de Flask de sondeos[/Jade]" en Visual Studio. Ha aprendido todos los conceptos básicos de Flask, como el uso de las vistas, las plantillas y el enrutamiento, y ha visto cómo se usan los almacenes de datos de copia de seguridad. Ahora podrá empezar a trabajar en una aplicación web propia con las vistas y los modelos que necesite.

La ejecución de una aplicación web en el equipo de desarrollo es solamente un paso en el proceso de poner la aplicación a disposición de sus clientes. Los pasos siguientes pueden incluir las siguientes tareas:

- Implementar la aplicación web en un servidor de producción, como Azure App Service. Consulte [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Agregue una implementación de repositorio que use otro almacén de datos de nivel de producción como PostgreSQL, MySQL o SQL Server (todos ellos se pueden hospedar en Azure). También puede usar el [SDK de Azure para Python](/python/azure/?view=azure-python) para trabajar con los servicios de almacenamiento de Azure, como tablas y blobs, así como Cosmos DB.

- Configurar una canalización de implementación continua/integración continua en un servicio como Azure DevOps. Además de funcionar con el control de código fuente (en Azure Repos, GitHub u otro servicio), puede configurar un proyecto de Azure DevOps para que ejecute automáticamente pruebas unitarias como requisito previo para la publicación y también configurar la canalización para implementar en un servidor de ensayo para pruebas adicionales antes de implementar en producción. Azure DevOps, además, se integra con soluciones de supervisión como App Insights y cierra todo el ciclo con herramientas de planeación de Ágil. Para obtener más información, consulte [Creación de una canalización de CI/CD para Python con Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts) y también la [Azure DevOps Documentation](/azure/devops/?view=vsts) (Documentación de Azure DevOps) general.
