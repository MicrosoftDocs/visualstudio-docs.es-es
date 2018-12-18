---
title: Publicación de una aplicación de Python en Azure App Service en Windows
description: Describe cómo publicar una aplicación web de Python directamente en Azure App Service en Windows desde Visual Studio, incluido el contenido necesario para el archivo web.config.
ms.date: 10/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: cae15da8b6a59587037171ae982ee77d2cce2861
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459967"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publicación en Azure App Service en Windows

> [!Note]
> Este contenido y las características que se describen están en desuso, pero siguen funcionando. Se recomienda que los desarrolladores de Python migren a [App Service en Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) siempre que sea posible.

Visual Studio ofrece la posibilidad de publicar una aplicación web de Python directamente en Azure App Service en Windows. Publicar en Azure App Service en Windows implica copiar los archivos necesarios en el servidor y configurar un archivo `web.config` apropiado que indique al servidor web cómo lanzar la aplicación.

El proceso de publicación difiere entre Visual Studio 2017 y Visual Studio 2015. En concreto, Visual Studio 2015 automatiza algunos de los pasos, incluida la creación de `web.config`, pero esta automatización limita la flexibilidad y el control a largo plazo. Visual Studio 2017 requiere más pasos manuales, pero ofrece un control más exacto sobre el entorno de Python. Aquí se describen ambas opciones.

> [!Note]
> Para obtener información sobre los cambios entre Visual Studio 2015 y Visual Studio 2017, consulte la entrada de blog [Publish to Azure in Visual Studio 2017 (Publicar en Azure en Visual Studio 2017)](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Requisitos previos

Para este tutorial, necesita un proyecto de aplicación web basado en las plataformas Bottle, Flask o Django. Si aún no tiene un proyecto y le gustaría probar el proceso de publicación, cree un proyecto de prueba sencillo de la siguiente forma:

1. En Visual Studio, seleccione **Archivo > Nuevo > Proyecto**, busque "Bottle", seleccione **Proyecto web de Bottle**, especifique y asigne una ruta de acceso para el proyecto y haga clic en **Aceptar**. (La plantilla de Bottle se incluye con la carga de trabajo de desarrollo de Python; consulte [Instalación](installing-python-support-in-visual-studio.md)).

1. Siga las indicaciones para instalar los paquetes externos, y seleccione **Instalar en un entorno virtual** y el intérprete base que prefiera para el entorno virtual. Por lo general, coincide con la versión de Python instalada en App Service.

1. Pruebe el proyecto de forma local pulsando F5 o seleccionando **Depurar > Iniciar depuración**.

## <a name="create-an-azure-app-service"></a>Crear un Azure App Service

Para publicar en Azure, se requiere un App Service de destino. Para ello, puede crear un App Service usando una suscripción de Azure o puede usar un sitio temporal.

Si aún no tiene una suscripción, comience con una [cuenta completa de Azure gratuita](https://azure.microsoft.com/free/), que incluye numerosos créditos para servicios de Azure. Considere también la posibilidad de registrarse para [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), que le ofrece un crédito de 25 USD cada mes durante un año completo.

> [!Tip]
> Aunque Azure solicita una tarjeta de crédito para comprobar su cuenta, no se realizará ningún cargo. También puede establecer un [límite de gasto](/azure/billing/billing-spending-limit) igual a sus créditos gratuitos para garantizar que no se realiza ningún cargo adicional. Además, Azure proporciona un nivel gratuito de plan de App Service que resulta ideal para aplicaciones de prueba sencillas, tal y como se describe en la siguiente sección.

### <a name="using-a-subscription"></a>Usar una suscripción

Con una suscripción activa de Azure, cree un App Service con una aplicación web vacía de la siguiente forma:

1. Inicie sesión en [portal.azure.com](https://portal.azure.com).
1. Seleccione **+Nuevo** y luego **Web y móvil** seguido de **Aplicación web**.
1. Especifique un nombre para la aplicación web, deje **Grupo de recursos** como "Crear nuevo" y elija **Windows** como el sistema operativo.
1. Seleccione **Plan de App Service/Ubicación**, seleccione **Crear nuevo** y especifique un nombre y una ubicación. Luego, seleccione **Plan de tarifa**, desplácese hacia abajo y seleccione el plan **F1 Free**, pulse **Seleccionar**, **Aceptar** y luego **Crear**.
1. (Opcional) Una vez creado el App Service, navegue hacia él, seleccione **Obtener perfil de publicación** y guarde el archivo de forma local.

### <a name="using-a-temporary-app-service"></a>Usar un App Service temporal

Cree un App Service temporal sin necesidad de una suscripción de Azure siguiendo estos pasos:

1. Abra el explorador en [try.azurewebsites.net](https://try.azurewebsites.net).
1. Seleccione **Aplicación web** para el tipo de aplicación, a continuación, seleccione **Siguiente**.
1. Seleccione **Empty Site** (Sitio vacío) y luego **Crear**.
1. Inicie sesión con el inicio de sesión social que prefiera y, después de un breve período de tiempo, el sitio está listo en la dirección URL mostrada.
1. Seleccione **Descargar el perfil de publicación** y guarde el archivo `.publishsettings`, que usa más adelante.

## <a name="configure-python-on-azure-app-service"></a>Configurar Python en Azure App Service

Una vez que tenga un App Service con una aplicación web vacía ejecutándose (en su suscripción o en un sitio gratuito), instale la versión que desee de Python tal y como se describe en [Administrar Python en Azure App Service](managing-python-on-azure-app-service.md). Para publicar desde Visual Studio 2017, registre la ruta exacta al intérprete de Python instalado con la extensión de sitio de la forma que se describe en ese artículo.

Si lo desea, también puede instalar el paquete `bottle` siguiendo el proceso de dichas instrucciones, ya que ese paquete se instala como parte de otros pasos en este tutorial.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publicar en App Service: Visual Studio 2017

Al publicar en Azure App Service desde Visual Studio 2017, solo se copian los archivos de su proyecto en el servidor. Por tanto, se deben crear los archivos necesarios para configurar el entorno del servidor.

1. En el **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto y seleccione **Agregar > Nuevo elemento*. En el cuadro de diálogo que aparece, seleccione la plantilla "Azure web.config (Fast CGI)" y, luego, Aceptar. De esta forma, se crea un archivo `web.config` en la raíz del proyecto.

1. Modifique la entrada `PythonHandler` en `web.config`, para que la ruta de acceso coincida con la instalación de Python en el servidor; vea la [referencia sobre la configuración de IIS](https://www.iis.net/configreference) (iis.net) para conocer los detalles exactos. Por ejemplo, para Python 3.6.1 x64, la entrada debería aparecer de esta forma:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Establezca la entrada `WSGI_HANDLER` de `web.config` de forma adecuada para el marco que esté usando:

    - **Bottle**: agregue paréntesis después de `app.wsgi_app`, tal y como se muestra abajo. Esto resulta necesario porque ese objeto es una función (vea `app.py`) en lugar de una variable:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: cambie el valor `WSGI_HANDLER` a `<project_name>.app`, donde `<project_name>` coincide con el nombre del proyecto. Puede encontrar el identificador exacto examinando la instrucción `from <project_name> import app` en `runserver.py`. Por ejemplo, si el proyecto se denominara "FlaskAzurePublishExample", la entrada aparecería así:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: se requieren dos cambios en `web.config` para los proyectos de Django. En primer lugar, cambie el valor `WSGI_HANDLER` a `django.core.wsgi.get_wsgi_application()` (el objeto está en el archivo `wsgi.py`):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        En segundo lugar, agregue la siguiente entrada debajo de la de `WSGI_HANDLER`, reemplazando `DjangoAzurePublishExample` por el nombre del proyecto:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Solo para las aplicaciones de Django**: en el archivo `settings.py` del proyecto de Django, agregue el dominio de dirección URL del sitio a `ALLOWED_HOSTS` tal y como se muestra más abajo, sustituyendo 'vspython-test-02.azurewebsites.net' por su URL:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Si no agrega la URL a la matriz, se genera el error "DisallowedHost at / Invalid HTTP_HOST header: '\<URL del sitio\>'. Es posible que deba agregar '\<URL del sitio\>' a ALLOWED_HOSTS".

    Tenga en cuenta que, cuando la matriz está vacía, Django permite automáticamente 'localhost', pero con la adición de la dirección URL de producción se eliminan dichas funcionalidades. Por este motivo, puede que desee mantener copias de desarrollo y producción independientes de `settings.py`, o bien usar variables de entorno para controlar los valores de tiempo de ejecución.

1. En el **Explorador de soluciones**, expanda la carpeta con el mismo nombre que el proyecto, haga clic con el botón derecho en la carpeta `static`, seleccione **Agregar > Nuevo elemento**, seleccione la plantilla "Archivos estáticos de Azure web.config" y seleccione **Aceptar**. Esta acción crea otro `web.config` en la carpeta `static` que deshabilita el procesamiento de Python para esa carpeta. Esta configuración envía solicitudes de archivos estáticos al servidor web predeterminado en lugar de usar la aplicación de Python.

1. Guarde el proyecto y, luego, en el **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

    ![Comando Publicar en el menú contextual de un proyecto](media/template-web-publish-command.png)

1. En la ficha **Publicar** que aparece, seleccione el destino de publicación:

    a. Su propia suscripción de Azure: seleccione **Microsoft Azure App Service**, **Seleccionar existente** y **Publicar**. Aparecerá un cuadro de diálogo en el que podrá seleccionar la suscripción y el App Service adecuados. Si el App Service no aparece, use el perfil de publicación descargado tal como se describe más abajo para usar un App Service temporal.

    ![Paso 1 de la publicación en Azure con Visual Studio 2017 y suscripciones existentes](media/tutorials-common-publish-1a-2017.png)

    b. Si usa un App Service temporal en try.azurewebsites.net o necesita usar un perfil de publicación, seleccione el control **>** para buscar **Importar perfil**, seleccione esa opción y, luego, seleccione **Publicar**. Esto solicita la ubicación del archivo `.publishsettings` descargado anteriormente.

    ![Paso 1 de la publicación en Azure con Visual Studio 2017 y App Service temporal](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio muestra el estado de publicación en una ventana "Actividad de publicación web" y la ventana Publicar. Una vez completada la publicación, se abre el explorador predeterminado en la dirección URL del sitio. La dirección URL también se muestra en la ventana Publicar.

1. Cuando se abra el explorador, es posible que vea el mensaje "No se puede mostrar la página. Error interno en el servidor". Este mensaje indica que el entorno de Python en el servidor no está completamente configurado, en cuyo caso siga estos pasos:

    a. Consulte de nuevo [Administrar Python en Azure App Service](managing-python-on-azure-app-service.md), asegurándose de que tiene una extensión de sitio de Python adecuada instalada.

    b. Compruebe la ruta al intérprete de Python en el archivo `web.config`. La ruta debe coincidir exactamente con la ubicación de instalación de la extensión de sitio elegida.

    c. Use la consola de Kudu para actualizar los paquetes incluidos en el archivo `requirements.txt` de la aplicación: navegue a la misma carpeta de Python que se usa en `web.config`, como `/home/python361x64`, y ejecute el siguiente comando tal y como se describe en la sección de la [consola de Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console):

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Si obtiene errores de permisos al ejecutar este comando, compruebe que está ejecutando el comando en la carpeta de la extensión de sitio y *no* en la carpeta de una de las instalaciones de Python predeterminadas de App Service. Dado que no se pueden modificar esos entornos predeterminados, se producirá un error al intentar instalar paquetes.

    d. Para obtener una salida de error detallada, agregue la siguiente línea a `web.config` dentro del nodo `<system.webServer>`, que proporciona una salida de error más detallada:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Pruebe a reiniciar el App Service después de instalar nuevos paquetes. No es necesario reiniciar al cambiar `web.config`, ya que el App Service realiza un reinicio automático cada vez que cambia `web.config`.

    > [!Tip]
    > Si realiza algún cambio en el archivo `requirements.txt` de la aplicación, asegúrese de usar de nuevo la consola de Kudu para instalar cualquier paquete que esté ahora incluido en ese archivo.

1. Cuando haya configurado por completo el entorno del servidor, actualice la página en el navegador y deberá aparecer la aplicación web.

    ![Resultados de publicar aplicaciones de Bottle, Flask y Django en App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publicar en App Service: Visual Studio 2015

> [!Note]
> Puede ver un breve vídeo de este proceso en [Visual Studio Python Tutorial: Building a Website (Tutorial de Python en Visual Studio: compilar un sitio web)](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3 min 10 s).

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

1. En el cuadro de diálogo **Publicar**, seleccione **Microsoft Azure App Service**:

  ![Publicar en Azure - Paso 1](media/tutorials-common-publish-1.png)

1. Seleccione un destino:

    - Si tiene una suscripción de Azure, seleccione **Microsoft Azure App Service** como el destino de publicación y luego, en el cuadro de diálogo siguiente, seleccione un servicio de aplicación existente o **Nuevo** para crear uno nuevo.
    - Si utiliza un sitio temporal de try.azurewebsites.net, seleccione **Importar** como el destino de publicación y luego busque el archivo `.publishsettings` descargado del sitio y seleccione **Aceptar**.

1. Los detalles de App Service aparecen en la pestaña **Conexión** del cuadro de diálogo **Publicar** que se muestra a continuación.

  ![Publicar en Azure - Paso 2](media/tutorials-common-publish-2.png)

1. Seleccione **siguiente >** según sea necesario para revisar la configuración adicional.

1. Seleccione **Publicar**. Una vez implementada la aplicación en Azure, se abre el explorador predeterminado en ese sitio.

Como parte de este proceso, Visual Studio también realiza los siguientes pasos:

- Crear un archivo `web.config` en el servidor que contiene punteros adecuados a la función `wsgi_app` de la aplicación y al intérprete predeterminado Python 3.4 de App Service.
- Desactivar el procesamiento de archivos en la carpeta `static` del proyecto (las reglas para esto están en `web.config`).
- Publicar el entorno virtual en el servidor.
- Agregar un archivo `web.debug.config` y las herramientas de depuración ptvsd para habilitar la depuración remota.

Tal y como se indicó anteriormente, estos pasos automáticos simplifican el proceso de publicación, pero hacen que sea más difícil controlar el entorno de Python. Por ejemplo, el archivo `web.config` se crea solo en el servidor, pero no se agrega al proyecto. El proceso de publicación también tarda más, ya que copia todo el entorno virtual desde el equipo de desarrollo en lugar de confiar en la configuración del servidor.

Finalmente, es posible que desee mantener su propio archivo `web.config` y usar `requirements.txt` para mantener los paquetes en el servidor directamente. En concreto, el uso de `requirements.txt` garantiza que los entornos de servidor y desarrollo siempre coincidan.
