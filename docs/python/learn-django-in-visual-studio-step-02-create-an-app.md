---
title: Información sobre el paso 2 del tutorial de Django en Visual Studio, vistas y plantilla de página
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio,en particular los pasos para crear una aplicación y utilizar vistas y plantillas.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 8d91e587f354efe14db7cd669fa89a0f4658a538
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90097312"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Paso 2: Creación de una aplicación de Django con vistas y plantillas de página

**Paso anterior: [Creación de una solución y un proyecto de Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Lo que tiene hasta el momento en el proyecto de Visual Studio son solo los componentes de nivel de sitio de un *proyecto* de Django, que puede ejecutar una o varias *aplicaciones* de Django. El siguiente paso consiste en crear su primera aplicación con una sola página.

En este paso aprenderá lo siguiente:

> [!div class="checklist"]
> - Crear una aplicación de Django con una sola página (paso 2.1)
> - Ejecutar la aplicación desde el proyecto de Django (paso 2.2)
> - Representar una vista mediante HTML (paso 2.3)
> - Representar una vista utilizando una plantilla de página de Django (paso 2.4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Paso 2-1: Creación de una aplicación con una estructura predeterminada

Una aplicación de Django es un paquete de Python independiente que contiene un conjunto de archivos relacionados para un propósito específico. Un proyecto de Django puede contener cualquier número de aplicaciones, lo que refleja el hecho de que un host de web puede atender cualquier número de puntos de entrada independientes desde un único nombre de dominio. Por ejemplo, es posible que un proyecto de Django para un dominio como contoso.com contenga una aplicación para `www.contoso.com`, una segunda aplicación para support.contoso.com y una tercera para docs.contoso.com. En este caso, el proyecto de Django controla el enrutamiento y la configuración de direcciones URL de nivel de sitio (en sus archivos *urls.py* y *settings.py*), mientras que cada aplicación tiene su propio estilo y comportamiento distintivo definidos por su enrutamiento interno, vistas, modelos, archivos estáticos e interfaz administrativa.

Normalmente, una aplicación de Django comienza con un conjunto estándar de archivos. Visual Studio proporciona plantillas de elementos para inicializar una aplicación de Django dentro de un proyecto de Django, junto con un comando de menú integrado que tiene la misma finalidad:

- Plantillas: En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento**, seleccione la plantilla **Aplicación Django 1.9**, especifique el nombre de la aplicación en el campo **Nombre** y haga clic en **Aceptar**.

- Comando integrado: En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Aplicación de Django**. Este comando le pide un nombre y crea una aplicación de Django 1.9.

    ![Comando de menú para agregar una aplicación de Django](media/django/step02-add-django-app-command.png)

Con cualquiera de estos métodos, cree una aplicación con el nombre "HelloDjangoApp". El resultado es una carpeta en el proyecto con ese nombre que contiene elementos como se describe en la tabla siguiente.

![Archivos de la aplicación de Django en el Explorador de soluciones](media/django/step02-django-app-in-solution-explorer.png)

| Elemento | Descripción |
| --- | --- |
| **\_\_init\_\_.py** | El archivo que identifica la aplicación como un paquete. |
| **migrations** | Una carpeta en la que Django almacena los scripts que actualizan la base de datos para adaptarlos a los cambios de los modelos. Las herramientas de migración de Django aplican entonces los cambios necesarios a cualquier versión anterior de la base de datos para que coincida con los modelos actuales. Con las migraciones, mantiene el foco en los modelos y permite que Django controle el esquema de base de datos subyacente. Las migraciones se tratan en el paso 6; por ahora, la carpeta contiene simplemente un archivo *\_\_init\_\_.py* (que indica que la carpeta define su propio paquete de Python). |
| **templates** | Carpeta para las plantillas de página de Django que contienen un único archivo *index.html* dentro de una carpeta que coincide con el nombre de la aplicación. (En Visual Studio 2017 15.7 y versiones anteriores, el archivo se encuentra directamente en *Plantillas* y en los pasos del 2 al 4 se insta al usuario a crear la subcarpeta). Las plantillas son bloques de HTML en las que las vistas pueden agregar información para representar una página de forma dinámica. Las "variables" de la plantilla de la página, como `{{ content }}` en *index.html*, son marcadores de posición para valores dinámicos, como se explica más adelante en este artículo (paso 2). Las aplicaciones de Django normalmente crean un espacio de nombres colocándolas en una subcarpeta que coincida con el nombre de la aplicación. |
| **admin.py** | El archivo de Python en el que amplía la interfaz administrativa de la aplicación (vea el paso 6), que se usa para inicializar y editar datos en una base de datos. Inicialmente, este archivo contiene solo la instrucción, `from django.contrib import admin`. De forma predeterminada, Django incluye una interfaz de administración estándar a través de entradas en el archivo *settings.py* del proyecto de Django, que puede activar quitando las marcas de comentario de las entradas existentes en *urls.py*. |
| **apps.py** | Un archivo de Python que define una clase de configuración para la aplicación (vea a continuación, después de esta tabla). |
| **models.py** | Los modelos son objetos de datos, identificados por funciones, a través de los cuales las vistas interactúan con la base de datos subyacente de la aplicación (vea el paso 6). Django proporciona el nivel de conexión de base de datos para que las aplicaciones no tengan que preocuparse por estos detalles. El archivo *models.py* es una ubicación predeterminada para crear los modelos, e inicialmente contiene solo la instrucción, `from django.db import models`. |
| **tests.py** | Un archivo de Python que contiene la estructura básica de las pruebas unitarias. |
| **views.py** | Las vistas son lo que se suele considerar páginas web, que toman una solicitud HTTP y devuelven una respuesta HTTP. Las vistas suelen representarse como código HTML que los exploradores web saben cómo mostrar, pero una vista no tiene necesariamente que ser visible (por ejemplo, un formulario intermedio). Una vista se define mediante una función de Python cuya responsabilidad es representar el código HTML que se enviará al explorador. El archivo *views.py* es una ubicación predeterminada para crear vistas, e inicialmente contiene solo la instrucción, `from django.shortcuts import render`. |

El contenido de *apps.py* aparece del modo siguiente cuando se usa el nombre "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿La creación de una aplicación de Django en Visual Studio es diferente de la creación de una aplicación en la línea de comandos?

Respuesta: La ejecución del comando **Agregar** > **Aplicación de Django** o el uso de **Agregar** > **Nuevo elemento** con una plantilla de aplicación de Django genera los mismos archivos que el comando de Django `manage.py startapp <app_name>`. La ventaja de crear la aplicación en Visual Studio es que la carpeta de la aplicación y todos sus archivos se integran automáticamente en el proyecto. Puede usar el mismo comando de Visual Studio para crear cualquier número de aplicaciones en el proyecto.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Paso 2-2: Ejecución de la aplicación desde el proyecto de Django

En este punto, si ejecuta el proyecto de nuevo en Visual Studio (con el botón de la barra de herramientas o **Depurar** > **Iniciar depuración**), seguirá viendo la página predeterminada. No aparece ningún contenido de la aplicación porque debe definir una página específica de la aplicación y agregar la aplicación al proyecto de Django:

1. En la carpeta *HelloDjangoApp*, modifique *views.py* para que coincida con el código siguiente, que define una vista denominada "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. En la carpeta *BasicProject* (creada en el paso 1), modifique *urls.py* para que al menos coincida con el código siguiente (puede conservar los comentarios instructivos si quiere):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Cada modelo de dirección URL describe las vistas a las que Django enruta las direcciones URL relativas al sitio específicas (es decir, la parte que sigue a `https://www.domain.com/`). La primera entrada de `urlPatterns` que comienza con la expresión regular `^$` es el enrutamiento para la raíz del sitio, "/". La segunda entrada, `^home$` específicamente enruta "/home". Puede tener cualquier número de enrutamientos a la misma vista.

1. Ejecute el proyecto de nuevo para ver el mensaje **Hello, Django!** definido por la vista. Cuando haya terminado, detenga el servidor.

### <a name="commit-to-source-control"></a>Confirmación en el control de código fuente

Dado que ha realizado cambios en el código y ha probado que funcionan correctamente, ahora es un buen momento para revisar y confirmar los cambios en el control de código fuente. Los pasos posteriores de este tutorial le recuerdan los momentos adecuados para volver a confirmar el control de código fuente, y le remiten a esta sección.

1. Seleccione el botón de cambios de la parte inferior de Visual Studio (en un círculo abajo), que le lleva a **Team Explorer**.

    ![Botón de cambios de control de código fuente en la barra de estado de Visual Studio](media/django/step02-source-control-changes-button.png)

1. En **Team Explorer**, escriba un mensaje de confirmación como "Crear la aplicación inicial de Django" y seleccione **Confirmar todo**. Una vez que se haya completado la confirmación, verá un mensaje **Confirmar \<hash> de creación local. Sincronizar para compartir los cambios con el servidor.** Si desea insertar los cambios en el repositorio remoto, seleccione **Sincronizar** y luego **Insertar** en **Confirmaciones de salida**. También puede acumular varias confirmaciones locales antes de insertar en la instancia remota.

    ![Inserción de confirmaciones en instancia remota en Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Para qué sirve el prefijo "r" que aparece delante de las cadenas de enrutamiento?

Respuesta: El prefijo "r" en una cadena de Python significa "raw" (sin formato), lo que indica a Python que no trate como escape ninguno de los caracteres de la cadena. Dado que las expresiones regulares usan muchos caracteres especiales, el prefijo "r" hace que esas cadenas sean mucho más fáciles de leer que si contuvieran una serie de caracteres de escape "\\".

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Qué significan los caracteres ^ y $ en las entradas de enrutamiento de dirección URL?

Respuesta: En las expresiones regulares que definen patrones de dirección URL, ^ significa "inicio de línea" y $ significa "final de línea," donde de nuevo las direcciones URL se refieren a la raíz del sitio (la parte que sigue a `https://www.domain.com/`). La expresión regular `^$` significa "en blanco" y, por tanto, coincide con la dirección URL completa `https://www.domain.com/` (no se agrega nada a la raíz del sitio). El patrón `^home$` coincide exactamente con `https://www.domain.com/home/`. (Django no usa la barra / final en detección de patrones).

Si no utiliza el carácter $ final en una expresión regular, como en `^home`, el patrón de la dirección URL coincide con *cualquier* dirección URL que comience por "home" , como "home", "homework", "homestead" y "home192837".

Para experimentar con diferentes expresiones regulares, pruebe herramientas en línea como [regex101.com](https://regex101.com) en [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Paso 2-3: Representación de una vista mediante HTML

La función `index` que tiene de momento en *views.py* solo genera una respuesta HTTP en texto sin formato para la página. La mayoría las páginas web reales, por supuesto, responden con páginas HTML enriquecidas que a menudo incorporan datos en directo. De hecho, la razón principal para definir una vista usando una función es que pueda generar ese contenido dinámicamente.

Dado que el argumento `HttpResponse` es simplemente una cadena, es posible crear cualquier HTML que desee dentro de una cadena. Como ejemplo sencillo, reemplace la función `index` por el código siguiente (manteniendo las instrucciones `from` existentes), lo cual genera una respuesta HTML con contenido dinámico que se actualiza cada vez que actualice la página:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Ejecute el proyecto nuevo, para ver un mensaje como "**Hello Django!** el lunes, 16 de abril de 2018 a las 16:28:10". Actualice la página para actualizar la hora y confirme que el contenido se genera con cada solicitud. Cuando haya terminado, detenga el servidor.

> [!Tip]
> Un acceso directo para detener y reiniciar el proyecto es usar el comando de menú **Depurar** > **Reiniciar** (**Ctrl**+**Mayús**+**F5**) o el botón **Reiniciar** de la barra de herramientas de depuración:
>
> ![Botón Reiniciar en la barra de herramientas de depuración en Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Paso 2-4: Representación de una vista mediante una plantilla de página

La generación de HTML en el código funciona perfectamente en páginas muy pequeñas, pero a medida que las páginas sean más sofisticadas, querrá mantener las partes HTML estáticas de la página (junto con las referencias a archivos CSS y JavaScript) como "plantillas de página" en las que podrá insertar contenido dinámico generado por el código. En la sección anterior, solo la fecha y hora de la llamada `now.strftime` son dinámicos, lo que significa que todo el contenido se puede colocar en una plantilla de página.

Una plantilla de página de Django es un bloque de código HTML que puede contener cualquier número de tokens de reemplazo denominados "variables" que se delimitan por `{{` y `}}`, como en `{{ content }}`. El módulo de creación de plantillas de Django reemplaza entonces las variables por el contenido dinámico que proporciona en el código.

En los pasos siguientes se muestra el uso de las plantillas de página:

1. En la carpeta *BasicProject*, que contiene el proyecto de Django, abra el archivo *settings.py* y agregue el nombre de la aplicación, "HelloDjangoApp", a la lista `INSTALLED_APPS`. Con la adición de la aplicación a la lista se indica al proyecto de Django que hay una carpeta con ese nombre que contiene una aplicación:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Además, en *settings.py*, asegúrese de que el objeto `TEMPLATES` contiene la siguiente línea (incluida de forma predeterminada), que indica a Django que busque plantillas en la carpeta *templates* de una aplicación instalada:

    ```json
    'APP_DIRS': True,
    ```

1. En la carpeta *HelloDjangoApp*, abra el archivo de plantilla de página *templates/HelloDjangoApp/index.html* (o *templates/index.html* en VS 2017 15.7 y versiones anteriores)para observar que contiene una variable, `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. En la carpeta *HelloDjangoApp*, abra *views.py* y reemplace la función `index` por el siguiente código que usa la función del asistente `django.shortcuts.render`. El asistente `render` proporciona una interfaz simplificada para trabajar con plantillas de página. Asegúrese de mantener todas las instrucciones `from` existentes.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    El primer argumento para `render`, como puede ver, es el objeto de solicitud, seguido de la ruta de acceso relativa al archivo de plantilla dentro de la carpeta *templates* de la aplicación. Se asigna a un archivo de plantilla el nombre de la vista que admite, si procede. El tercer argumento para `render` es un diccionario de variables al que hace referencia la plantilla. Puede incluir objetos en el diccionario, en cuyo caso una variable de la plantilla puede hacer referencia a `{{ object.property }}`.

1. Ejecute el proyecto y observe la salida. Verá un mensaje similar al del paso 2.2, que indica que la plantilla funciona.

    Sin embargo, tenga en cuenta que el código HTML que usó en la propiedad `content` se representa solo como texto sin formato porque la función `render` convierte automáticamente en escape ese HTML. El escape automático evita vulnerabilidades accidentales en los ataques por inyección de código: los desarrolladores suelen recopilar información de una página y emplearla como valor en otra mediante un marcador de posición de plantilla. El escape también sirve como recordatorio de que es mejor conservar el HTML en la plantilla de página y fuera del código. Por suerte, resulta sencillo crear variables adicionales cuando es necesario. Por ejemplo, cambie *index.html* por *templates* para que coincida con el siguiente marcado, que agrega un título de página y mantiene todo el formato de la plantilla de página:

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

    A continuación, escriba la función de vista `index` como sigue, para proporcionar valores para todas las variables en la plantilla de página:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Detenga el servidor y reinicie el proyecto, y observe que la página ahora se representa correctamente:

    ![Ejecución de la aplicación con la plantilla](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 15.7 y versiones anteriores: Como paso final, mueva las plantillas a una subcarpeta con el mismo nombre que la aplicación, que crea un espacio de nombres y evita posibles conflictos con otras aplicaciones que es posible que se agreguen al proyecto. (Las plantillas en VS 2017 15.8+ hacen esto automáticamente). Es decir, cree una subcarpeta en *templates* denominada *HelloDjangoApp*, mueva *index.html* a esa subcarpeta y modifique la función de vista `index` para que haga referencia a la nueva ruta de acceso de la plantilla, *HelloDjangoApp/index.html*. A continuación, ejecute el proyecto, compruebe que la página se representa correctamente y detenga el servidor.

1. Confirme los cambios en el control de código fuente y actualice su repositorio remoto, si lo desea, tal y como se describe en el [paso 2.2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Las plantillas de página deben estar en un archivo independiente?

Respuesta: Aunque las plantillas normalmente se guardan en archivos HTML independientes, también se puede usar una plantilla insertada. No obstante, se recomienda usar un archivo independiente para mantener una separación clara entre código y marcado.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Deben usar las plantillas la extensión de archivo .html?

Respuesta: La extensión *.html* para archivos de plantilla de página es completamente opcional, ya que siempre puede identificar la ruta de acceso exacta relativa al archivo en el segundo argumento para la función `render`. Pero Visual Studio (y otros editores) normalmente ofrecen características como la finalización de código y el coloreado de sintaxis con archivos *.html*, lo que compensa con creces el hecho de que las plantillas de página no sean estrictamente HTML.

De hecho, cuando esté trabajando con un proyecto de Django, Visual Studio detecta automáticamente cuándo el archivo HTML que está editando es realmente una plantilla de Django y proporciona algunas características de completado automático. Por ejemplo, al comenzar a escribir un comentario de plantilla de página de Django, `{#`, Visual Studio proporciona automáticamente los caracteres `#}` de cierre. Los comandos **Selección con comentarios** y **Selección sin comentarios** (en el menú **Editar** > **Opciones avanzadas** y en la barra de herramientas) también utilizan comentarios de plantilla en lugar de comentarios HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. Cuando ejecuto el proyecto, aparece un error que indica que no se encuentra la plantilla. ¿Qué ocurre?

Respuesta: Si ve errores que indican que no se encuentra la plantilla, asegúrese de que se ha agregado la aplicación al archivo *settings.py* del proyecto de Django en la lista `INSTALLED_APPS`. Sin esa entrada, Django no sabe que ha de buscar en la carpeta *templates* de la aplicación.

### <a name="question-why-is-template-namespacing-important"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Por qué es importante el espaciado entre nombres de la plantilla?

Respuesta: Cuando Django busca una plantilla a la que se hace referencia en la función `render`, usa el primer archivo que encuentre que coincida con la ruta de acceso relativa. Si tiene varias aplicaciones de Django en el mismo proyecto que utilizan las mismas estructuras de carpeta para las plantillas, es probable que una aplicación use involuntariamente una plantilla desde otra aplicación. Para evitar tales errores, cree siempre una subcarpeta bajo una carpeta *templates* de la aplicación que coincida con el nombre de la aplicación para evitar cualquier duplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Atender archivos estáticos, agregar páginas y usar la herencia de plantilla](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Escribiendo su primera aplicación en Django, parte 1: vistas](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Para conocer más funciones de las plantillas de Django, como la inclusión y la herencia, consulte [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (El lenguaje de plantilla de Django) (docs.djangoproject.com)
- [Regular expression training on inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (Entrenamiento de expresión regular en inLearning) (LinkedIn)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
