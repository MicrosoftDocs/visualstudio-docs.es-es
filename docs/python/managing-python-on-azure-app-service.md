---
title: "Instalación de intérpretes y bibliotecas de Python en Azure App Service | Microsoft Docs"
description: "Describe cómo instalar un intérprete y las bibliotecas de Python en Azure App Service y configuración de las aplicaciones web para que hagan referencia correctamente al intérprete."
ms.custom: 
ms.date: 09/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 0f0910459fecb01573b7282137949acbfd5dcb32
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="managing-python-on-azure-app-service"></a>Administrar Python en Azure App Service

[Azure App Service](https://azure.microsoft.com/services/app-service/) es una plataforma como servicio que se ofrece para las aplicaciones web, ya sean sitios a los que se acceda a través de un explorador, API de REST que usan sus propios clientes o procesamientos desencadenados por un evento. App Service admite completamente el uso de Python para implementar aplicaciones.

La compatibilidad de Python personalizable en Azure App Service se proporciona como un conjunto de *extensiones de sitio* de App Service en la que cada una contiene una versión específica del tiempo de ejecución de Python. Así, se pueden instalar los paquetes que se quiera directamente en ese entorno, como se describe en este artículo. Al personalizar el entorno en el propio App Service, no es necesario mantener los paquetes en los proyectos de aplicación web ni cargarlos con el código de la aplicación.

> [!Tip]
> Aunque App Service hace que Python 2.7 y Python 3.4 se instalen de forma predeterminada en las carpetas raíz del servidor, no se pueden personalizar ni instalar paquetes en esos entornos, ni tampoco conviene depender de su existencia o no. En su lugar, es mejor basarse en una extensión de sitio que pueda controlar, como se describe en este artículo.

> [!Important]
> Los procesos que se describen aquí están sujetos a cambios, y especialmente a mejoras. Los cambios se anuncian en [Ingeniería de Python en el blog de Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Elegir una versión de Python a través de Azure Portal

1. Cree un App Service de su aplicación web en Azure Portal.
1. En la página de App Service, vaya a la sección **Herramientas de desarrollo**, seleccione **Extensiones** y, después, **+ Agregar**.
1. Desplácese por la lista hasta encontrar la extensión que contiene la versión de Python que busca:

    ![Extensiones de Python en Azure Portal](media/python-on-azure-extensions.png)

    > [!Tip]
    > Si necesita una versión anterior de Python y no la ve en las extensiones de sitio, puede instalarla a través de Azure Resource Manager, tal y como se describe en la siguiente sección.

1. Seleccione la extensión, acepte los términos legales y, después, seleccione **Aceptar**.
1. Cuando la instalación finalice, aparecerá una notificación en el portal.

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Elegir una versión de Python a través de Azure Resource Manager

Si va a implementar App Service con una plantilla de Azure Resource Manager, agregue la extensión de sitio como un recurso. La extensión aparece como un recurso anidado con el tipo `siteextensions` y el nombre de [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Por ejemplo, después de agregar una referencia a `python361x64` (Python 3.6.1 x64), la plantilla puede tener el siguiente aspecto (algunas propiedades no se incluyen):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="setting-webconfig-to-point-to-the-python-interpreter"></a>Configuración de web.config para que apunte al intérprete de Python

Después de instalar la extensión de sitio (a través del portal o de una plantilla de Azure Resource Manager), lo siguiente es hacer que el archivo `web.config` de la aplicación apunte al intérprete de Python. El archivo `web.config` indica al servidor web de IIS (7+) que se ejecuta en App Service el modo en que debe administrar las solicitudes de Python a través de FastCGI o HttpPlatform.

Empiece buscando la ruta de acceso completa a la extensión de sitio `python.exe` y, luego, cree y modifique el archivo `web.config` correspondiente.

### <a name="finding-the-path-to-pythonexe"></a>Buscar la ruta de acceso apython.exe

Hay una extensión de sitio de Python instalada en el servidor en `d:\home`, en una carpeta adecuada a la versión y arquitectura de Python (excepto en el caso de algunas versiones anteriores). Por ejemplo, Python 3.6.1 x64 se instala en `d:\home\python361x64`. En este caso, la ruta al intérprete de Python sería `d:\home\python361x64\python.exe`.

Para ver la ruta de acceso específica en App Service, seleccione **Extensiones** en la página de App Service y seleccione la extensión en la lista.

![Lista de extensiones en Azure App Service](media/python-on-azure-extension-list.png)

Con esta acción se abre la página de descripción de la extensión que contiene la ruta de acceso:

![Información de extensiones en Azure App Service](media/python-on-azure-extension-detail.png)

Si tiene problemas para ver la ruta de acceso de la extensión, la puede encontrar manualmente a través de la consola:

1. En la página de App Service, seleccione **Herramientas de desarrollo > Consola**.
1. Escriba el comando `ls ../home` o `dir ..\home` para ver las carpetas de extensión de nivel superior, como `Python361x64`.
1. Escriba un comando como `ls ../home/python361x64` o `dir ..\home\python361x64` para confirmar que esa carpeta contiene `python.exe` y otros archivos de intérprete.

### <a name="configuring-the-fastcgi-handler"></a>Configurar el controlador FastCGI

FastCGI es una interfaz que funciona en el nivel de solicitud. IIS recibe conexiones entrantes y reenvía cada solicitud a una aplicación WSGI que se ejecuta en uno o más procesos de Python persistentes. El [paquete wfastcgi](https://pypi.io/project/wfastcgi) está preinstalado y configurado con cada extensión de sitio de Python, por lo que puede habilitarlo fácilmente incluyendo el código siguiente en `web.config`, como lo que se muestra aquí, perteneciente a una aplicación web basada en el marco Bottle. Observe que las rutas de acceso completas a `python.exe` y a `wfastcgi.py` se colocan en la clave `PythonHandler`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Los valores de `<appSettings>` aquí definidos están disponibles para la aplicación como variables de entorno:

- El valor de `PYTHONPATH` puede ampliarse libremente, pero debe incluir la raíz de la aplicación.
- `WSGI_HANDLER` debe apuntar a una aplicación WSGI que se pueda importar desde la aplicación.
- `WSGI_LOG` es opcional, pero es recomendable para depurar la aplicación. 

Vea [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) para obtener más detalles sobre el contenido de `web.config` para las aplicaciones web de Bottle, Flask y Django.

### <a name="configuring-the-httpplatform-handler"></a>Configurar el controlador de HttpPlatform

El módulo HttpPlatform pasa conexiones de socket directamente a un proceso de Python independiente. Ese paso a través le permite ejecutar cualquier servidor web que quiera, pero necesita un script de inicio que ejecute un servidor web local. Especifique el script en el elemento `<httpPlatform>` de `web.config`, donde el atributo `processPath` apunta al intérprete de Python de la extensión de sitio y el atributo `arguments`, a su script y a cualquier argumento que quiera proporcionar:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

## <a name="installing-packages"></a>Instalación de paquetes

El intérprete de Python instalado a través de una extensión de sitio es solo una parte del entorno de Python. Probablemente necesite instalar varios paquetes en ese entorno también.

Para instalar paquetes directamente en el entorno del servidor, emplee uno de los siguientes métodos:

| Métodos | Uso |
| --- | --- |
| [Consola de Kudu para Azure App Service](#azure-app-service-kudu-console) | Instala los paquetes de forma interactiva. Los paquetes deben ser Python puro o deben publicar paquetes wheel. |
| [API de REST de Kudu](#kudu-rest-api) | Se puede usar para automatizar la instalación de paquetes.  Los paquetes deben ser Python puro o deben publicar paquetes wheel. |
| Incluir con la aplicación | Instale paquetes directamente en el proyecto y, después, impleméntelos en App Service como si formasen parte de la aplicación. Dependiendo del número de dependencias que tenga y la frecuencia con la que las actualice, este método puede ser la manera más sencilla de obtener una implementación funcional. Conviene saber que estas bibliotecas deben coincidir con la versión de Python del servidor o, de lo contrario, verá errores poco conocidos tras la implementación. Dicho esto, como las versiones de Python en las extensiones de sitio de App Service son exactamente las mismas que las que se han presentado en python.org, puede obtener fácilmente una versión compatible para la implementación local. |
| Entornos virtuales | No se admite. En su lugar, use el método de inclusión y establezca la variable de entorno `PYTHONPATH` de forma que apunte a la ubicación de los paquetes. |

### <a name="azure-app-service-kudu-console"></a>Consola de Kudu para Azure App Service

La [consola de Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) le proporciona acceso de línea de comandos directo y con privilegios elevados al servidor de App Service y a su sistema de archivos. Aparte de ser una valiosa herramienta de depuración, también permite operaciones de CLI como la instalación de paquetes.

1. Abra Kudu desde la página de App Service en Azure Portal; para ello, seleccione **Herramientas de desarrollo > Herramientas avanzadas** y seleccione **Ir**. Con esta acción, se le llevará a una dirección URL similar a la dirección URL base de App Service, salvo que tiene insertado `.scm`. Por ejemplo, si la dirección URL base es `https://vspython-test.azurewebsites.net/`, Kudu está en `https://vspython-test.scm.azurewebsites.net/` (puede guardarla como marcador):

    ![La consola de Kudu para Azure App Service](media/python-on-azure-console01.png)

1. Seleccione **Consola de depuración > CMD** para abrir la consola, en la que puede navegar en su instalación de Python y ver qué bibliotecas ya están ahí.

1. Para instalar un único paquete:

    a. Vaya a la carpeta de la instalación de Python donde quiera instalar el paquete, como `d:\home\python361x64`.

    b. Use `python.exe -m pip install <package_name>` para instalar un paquete.

    ![Ejemplo de instalación de Bottle a través de la consola de Kudu para Azure App Service](media/python-on-azure-console02.png)

1. Si ya ha implementado un archivo `requirements.txt` para la aplicación en el servidor, instale todos esos requisitos del siguiente modo:

    a. Vaya a la carpeta de la instalación de Python donde quiera instalar el paquete, como `d:\home\python361x64`.

    b. Ejecute el comando `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Se recomienda usar `requirements.txt`, porque es sencillo reproducir el paquete exacto que se ha establecido tanto localmente como en el servidor. Recuerde simplemente ir a la consola después de implementar los cambios realizados en `requirements.txt` y volver a ejecutar el comando.

> [!Note]
> En App Service no existe ningún compilador de C, por lo que necesita instalar el paquete wheel para cualquier paquete con módulos de extensión nativos. Muchos paquetes conocidos proporcionan sus propias ruedas. Para los paquetes que no lo hacen, use `pip wheel <package_name>` en su equipo de desarrollo local y, después, cargue la rueda en su sitio. Para un ejemplo, consulte [Administración de los paquetes necesarios con requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>API de REST de Kudu

En lugar de usar la consola de Kudu mediante Azure Portal, puede ejecutar comandos de manera remota mediante la API de REST de Kudu publicando el comando en `https://yoursite.scm.azurewebsites.net/api/command`. Por ejemplo, para instalar el paquete `bottle`, publique el siguiente JSON en `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Para obtener información sobre los comandos y la autenticación, vea la [documentación de Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

También puede ver las credenciales usando el comando `az webapp deployment list-publishing-profiles` por medio de la CLI de Azure. Vea [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az_webapp_deployment_list_publishing_profiles). En [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42) hay disponible una biblioteca auxiliar para registrar comandos de Kudu.
