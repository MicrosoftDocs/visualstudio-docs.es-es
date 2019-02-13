---
title: Configuración de aplicaciones web de Python para IIS
description: Configuración de aplicaciones web de Python para ejecutarlas con Internet Information Services desde una máquina virtual Windows.
ms.date: 12/06/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 6a6861f2f334f3a03fe133e5185c9079a54cfb34
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937684"
---
# <a name="configure-python-web-apps-for-iis"></a>Configuración de aplicaciones web de Python para IIS

Cuando se usa Internet Information Services (IIS) como servidor web en un equipo Windows (incluidas [máquinas virtuales Windows en Azure](/azure/architecture/reference-architectures/n-tier/windows-vm), las aplicaciones de Python deben incluir una configuración específica en sus archivos *web.config* para que IIS pueda procesar correctamente el código Python. El equipo mismo también debe tener instalado Python junto con cualquier paquete que la aplicación web necesite.

> [!Note]
> Anteriormente, este artículo contenía guías para la configuración de Python en Azure App Service en Windows. Las extensiones de Python y los hosts de Windows que se usaban en ese escenario quedaron en desuso a favor de Azure App Service en Linux. Para más información, consulte [Publicación de una aplicación de Python en Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Sin embargo, todavía puede encontrar el artículo anterior en [Configuración de un entorno de Python en Azure App Service](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalación de Python en Windows

Para ejecutar una aplicación web, primero debe instalar la versión necesaria de Python directamente en la máquina host Windows, tal como se describe en [Instalación de intérpretes de Python](installing-python-interpreters.md).

Anote la ubicación del intérprete `python.exe` para pasos posteriores. Para mayor comodidad, puede agregar esa ubicación a la variable de entorno PATH.

## <a name="install-packages"></a>Instalar paquetes

Cuando se usa un host dedicado, puede usar el entorno global de Python para ejecutar la aplicación en lugar de un entorno virtual. En consecuencia, para instalar todos los requisitos de la aplicación en el entorno global, simplemente ejecute `pip install -r requirements.txt` en un símbolo del sistema.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Configuración de web.config para que apunte al intérprete de Python

El archivo *web.config* de la aplicación indica al servidor web de IIS (7+) que se ejecuta en Windows el modo en que debe administrar las solicitudes de Python a través de FastCGI o HttpPlatform. Cuando se usa Visual Studio 2017, debe modificar el archivo *web.config* de manera manual. Tal como se describe en una sección posterior, Visual Studio 2015 hace modificaciones

### <a name="configure-the-httpplatform-handler"></a>Configuración del controlador de HttpPlatform

El módulo HttpPlatform pasa conexiones de socket directamente a un proceso de Python independiente. Ese paso a través le permite ejecutar cualquier servidor web que quiera, pero necesita un script de inicio que ejecute un servidor web local. Especifique el script en el elemento `<httpPlatform>` de *web.config*, donde el atributo `processPath` apunta al intérprete de Python de la extensión de sitio y el atributo `arguments`, a su script y a cualquier argumento que quiera proporcionar:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

La variable de entorno `HTTP_PLATFORM_PORT` que se muestra aquí contiene el puerto en el que debe escuchar su servidor local para las conexiones del localhost. Este ejemplo también muestra cómo crear otra variable de entorno (si se quiere), que en este caso es `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Configuración del controlador FastCGI

FastCGI es una interfaz que funciona en el nivel de solicitud. IIS recibe conexiones entrantes y reenvía cada solicitud a una aplicación WSGI que se ejecuta en uno o más procesos de Python persistentes.

Para usarlo, primero instale y configure el paquete wfastcgi como se describe en [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

A continuación, modifique el archivo *web.config* para incluir las rutas de acceso completas a *python.exe* y *wfastcgi.py* en la clave `PythonHandler`. En los pasos que aparecen a continuación, se supone que Python está instalado en *c:\python36-32* y que el código de aplicación se encuentra en *c:\home\site\wwwroot*, por lo que debe ajustar las rutas de acceso según corresponda:

1. Modifique la entrada `PythonHandler` en *web.config* para que la ruta de acceso coincida con la ubicación de instalación de Python (consulte [Referencia de configuración de IIS](https://www.iis.net/configreference) (iis.net) para ver los detalles exactos).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. En la sección `<appSettings>` del archivo *web.config*, agregue claves para `WSGI_HANDLER`, `WSGI_LOG` (opcional) y `PYTHONPATH`:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Estos valores de `<appSettings>` están disponibles para la aplicación como variables de entorno:

    - El valor de `PYTHONPATH` puede ampliarse libremente, pero debe incluir la raíz de la aplicación.
    - `WSGI_HANDLER` debe apuntar a una aplicación WSGI que se pueda importar desde la aplicación.
    - `WSGI_LOG` es opcional, pero es recomendable para depurar la aplicación.

1. Establezca la entrada `WSGI_HANDLER` en *web.config* de forma adecuada para el marco que esté usando:

    - **Bottle**: asegúrese de usar paréntesis después de `app.wsgi_app` como se muestra a continuación. Esto resulta necesario porque ese objeto es una función (vea *app.py*) en lugar de una variable:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: cambie el valor `WSGI_HANDLER` por `<project_name>.app`, donde `<project_name>` coincide con el nombre del proyecto. Puede encontrar el identificador exacto examinando la instrucción `from <project_name> import app` en *runserver.py*. Por ejemplo, si el proyecto se denominara "FlaskAzurePublishExample", la entrada aparecería así:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: se requieren dos cambios en *web.config* para los proyectos de Django. En primer lugar, cambie el valor `WSGI_HANDLER` a `django.core.wsgi.get_wsgi_application()` (el objeto está en el archivo *wsgi.py*):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        En segundo lugar, agregue la siguiente entrada debajo de la de `WSGI_HANDLER`, reemplazando `DjangoAzurePublishExample` por el nombre del proyecto:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Solo para las aplicaciones de Django**: en el archivo *settings.py* del proyecto de Django, agregue el dominio de dirección URL del sitio o la dirección IP a `ALLOWED_HOSTS`, como se muestra más adelante, reemplazando, por supuesto, "1.2.3.4" con su dirección URL o su dirección IP:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Si no agrega la URL a la matriz, se genera el error **DisallowedHost at / Invalid HTTP_HOST header: "\<URL del sitio\>". Es posible que deba agregar "\<URL del sitio\>" a ALLOWED_HOSTS.**

    Tenga en cuenta que, cuando la matriz está vacía, Django permite automáticamente "localhost" y "127.0.0.1", pero agregar la dirección URL de producción quita esas funcionalidades. Por este motivo, puede que desee mantener copias de desarrollo y producción independientes de *settings.py*, o bien usar variables de entorno para controlar los valores de tiempo de ejecución.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Implementación en IIS o una máquina virtual Windows

Con el archivo *web.config* correcto en el proyecto, puede publicar en el equipo que ejecuta IIS si usa el comando **Publish** en el menú contextual del proyecto en el **Explorador de soluciones** y selecciona la opción **IIS, FTP, etc.**. En este caso, Visual Studio simplemente copia los archivos del proyecto en el servidor. Usted es responsable de toda la configuración del lado servidor.
