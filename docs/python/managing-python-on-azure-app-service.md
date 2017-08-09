---
title: Administrar Python en Azure App Service | Microsoft Docs
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 5b509a46dd3dbee3a45ab2eac57242636beee17b
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---

# <a name="managing-python-on-azure-app-service"></a>Administrar Python en Azure App Service

[Azure App Service](https://azure.microsoft.com/services/app-service/) es una plataforma como servicio que se ofrece para las aplicaciones web, ya sean sitios a los que se acceda a través de un explorador, API de REST que usan sus propios clientes o procesamientos desencadenados por un evento. App Service admite completamente el uso de Python para implementar aplicaciones.

La compatibilidad de Python en Azure App Service se proporciona como un conjunto de extensiones de sitio de App Service en la que cada una contiene una versión específica del runtime de Python. Obviamente se recomienda la última versión de Python 3, pero puede elegir una versión anterior si es necesario. En este tema se explica cómo instalar y configurar una extensión de sitio junto con cualquier paquete deseado.

> [!Note]
> Los procesos que se describen aquí están sujetos a cambios, y especialmente a mejoras. Los cambios se anuncian en [Ingeniería de Python en el blog de Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Elegir una versión de Python a través de Azure Portal

Si su sitio ya está implementado y ejecutándose en Azure App Service, vaya a su hoja de App Service, desplácese a la sección **Herramientas de desarrollo** y, después, seleccione **Extensiones > Agregar**. Desplácese por la lista para buscar las extensiones específicas de la versión de Python que quiera. (La lista no se puede ordenar, por lo que a menudo las distintas versiones están esparcidas por la lista):

![Extensiones de Python en Azure Portal](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Elegir una versión de Python a través de Azure Resource Manager

Si va a implementar su sitio con una plantilla de Azure Resource Manager, agregue la extensión de sitio como un recurso. La extensión aparece como un recurso anidado de su sitio con el tipo `siteextensions` y el nombre de [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Por ejemplo, después de agregar una referencia a `python361x64` (Python 3.6.1 x64), su plantilla puede tener el siguiente aspecto:

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
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
      ...
```

## <a name="configuring-your-site"></a>Configuración del sitio

Después de instalar la extensión de sitio (a través del portal o de una plantilla de Azure Resource Manager), la ruta de acceso de instalación de Python será algo como `d:\home\python361x64\python.exe`. Para ver la ruta específica, seleccione la extensión en la lista que se muestra para su App Service para abrir su página de descripción que contiene la ruta de acceso:

![Lista de extensiones en Azure App Service](media/python-on-azure-extension-list.png)

![Información de extensiones en Azure App Service](media/python-on-azure-extension-detail.png)

El siguiente paso es hacer referencia a la instalación de Python en el archivo `web.config` del sitio para los controladores de solicitudes de la plataforma HTTP y FastCGI.

### <a name="using-the-fastcgi-handler"></a>Usar el controlador de FastCGI

FastCGI es una interfaz que funciona en el nivel de solicitud. IIS recibe conexiones entrantes y reenvía cada solicitud a una aplicación WSGI que se ejecuta en uno o más procesos de Python persistentes. El [paquete wfastcgi](https://pypi.io/project/wfastcgi) está preinstalado y configurado con cada extensión de sitio de Python, por lo que puede habilitarlo fácilmente incluyendo el código siguiente en `web.config`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Los valores de `<appSettings>` están disponibles para la aplicación como variables de entorno:
- El valor de `PYTHONPATH` puede ampliarse libremente pero debe incluir la raíz de su sitio.
- `WSGI_HANDLER` debe apuntar a una aplicación WSGI que se pueda importar desde su sitio.
- `WSGI_LOG` es opcional pero se recomienda para la depuración de su sitio. 

En `<handlers>`, asegúrese de que el atributo `scriptProcessor` en el elemento `<add>` contiene las rutas adecuadas para su instalación específica. La ruta se muestra de nuevo en la hoja de información de la extensión.

### <a name="using-the-http-platform-handler"></a>Usar el controlar de la plataforma HTTP

El módulo HttpPlatform pasa las conexiones de socket directamente a un proceso de Python independiente. Ese paso a través le permite ejecutar cualquier servidor web que quiera, pero necesita un script de inicio que ejecute un servidor web local. Especifique el script en el elemento `<httpPlatform>`, donde el atributo `processPath` señala a Python y el atributo `arguments` señala a su script y a cualquier argumento que quiera proporcionar:

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

La ruta a `python.exe` en su configuración es, por supuesto, específica de la versión que ha instalado.

La variable de entorno `HTTP_PLATFORM_PORT` que se muestra en el código contiene el puerto en el que debe escuchar su servidor local para las conexiones del localhost. Este ejemplo también muestra cómo crear otra variable de entorno (si se quiere), que en este caso es `SERVER_PORT`.

## <a name="installing-packages"></a>Instalación de paquetes

Como probablemente su aplicación depende de una variedad de paquetes, necesita asegurarse de que esos paquetes están instalados en su entorno de Python en App Service mediante uno de estos tres métodos:

- La consola de Azure App Service en Azure Portal
- La API de REST de Kudu
- Copiar cada biblioteca en el código fuente de la aplicación

### <a name="kudu-console"></a>Consola de Kudu

La [consola de Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) le proporciona acceso de línea de comandos directo y con privilegios elevados al servidor de App Service y a su sistema de archivos. Además de ser una herramienta de depuración muy valiosa, también puede usarse para las configuraciones basadas en la CLI.

Acceda a Kudu desde la hoja de App Service seleccionando **Herramientas de desarrollo > Herramientas avanzadas**, después seleccione **Ir** para ir a una dirección URL que sea la misma que su URL base de App Service excepto con `.scm` insertado. Por ejemplo, si su URL base es `https://vspython-test.azurewebsites.net/`, entonces Kudu está en `https://vspython-test.scm.azurewebsites.net/`:

![La consola de Kudu para Azure App Service](media/python-on-azure-console01.png)

Seleccione **Consola de depuración > CMD** para abrir la consola, en la que puede navegar en su instalación de Python y ver qué bibliotecas ya están ahí.

Para instalar un único paquete:

1. Vaya a la carpeta de la instalación de Python donde quiera instalar el paquete, como `d:\home\python361x64`.
1. Use `python.exe -m pip install <package_name>` para instalar un paquete.

![Ejemplo de instalación de matplotlib mediante la consola de Kudu para Azure App Service](media/python-on-azure-console02.png)

Para instalar paquetes desde su `requirements.txt` (recomendado):

1. Vaya a la carpeta de la instalación de Python donde quiera instalar el paquete, como `d:\home\python361x64`.
1. Use `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` para instalar un paquete.

Se recomienda el uso de requirements.txt porque es sencillo reproducir el paquete exacto que se ha establecido tanto localmente como en el servidor.

> [!Note]
> No existe ningún compilador de C en su servidor web, por lo que necesita instalar la rueda para cualquier paquete con módulos de extensión nativos. Muchos paquetes conocidos proporcionan sus propias ruedas. Para los paquetes que no lo hacen, use `pip wheel <package_name>` en su equipo de desarrollo local y, después, cargue la rueda en su sitio. Para obtener un ejemplo, vea [Administración de paquetes necesarios](python-environments.md#managing-required-packages).

### <a name="kudu-rest-api"></a>API de REST de Kudu

En lugar de usar la consola de Kudu mediante Azure Portal, puede ejecutar comandos de manera remota mediante la API de REST de Kudu publicando el comando en `https://yoursite.scm.azurewebsites.net/api/command`. Por ejemplo, para instalar el paquete `matplotlib`, publique el siguiente JSON en `/api/command`:

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Para obtener información sobre los comandos y la autenticación, vea la [documentación de Kudu](https://github.com/projectkudu/kudu/wiki/REST-API). También puede ver credenciales con [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) desde la CLI de Azure. Una biblioteca auxiliar para publicar comandos de Kudu también está disponible en GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Copiar bibliotecas en el código fuente de la aplicación

En lugar de instalar paquetes directamente en el servidor, puede copiar bibliotecas en su propio código fuente e implementarlas como si formaran parte de su aplicación. Dependiendo del número de dependencias que tenga y la frecuencia con la que las actualice, este método puede ser la manera más sencilla de obtener una implementación funcional.

La advertencia es que estas bibliotecas deben coincidir exactamente con la versión de Python del servidor o, de lo contrario, verá errores poco conocidos tras la implementación. En cambio, como las versiones de Python en las extensiones de sitio de App Service son exactamente las mismas que las que se han presentado en python.org, puede obtener fácilmente una versión compatible para la implementación local.

### <a name="avoiding-virtual-environments"></a>Evitar entornos virtuales

Aunque trabajar en un entorno virtual localmente puede ayudarle a entender completamente las dependencias que necesita su sitio, con los entornos virtuales de App Service no se recomienda. En su lugar, simplemente instale bibliotecas en su carpeta de Python principal e impleméntelas con su aplicación para evitar tener dependencias en conflicto.
