---
title: Depuración remota de Azure con Python
description: Describe cómo configurar una instancia de Azure App Service para usar Visual Studio para la depuración remota de una aplicación de Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008624"
---
# <a name="remotely-debug-python-code-on-azure"></a>Depurar código de Python en Azure de forma remota

[La compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md) incluye la posibilidad de depurar de forma remota el código de Python que se ejecuta en Azure App Service. A diferencia de la depuración remota simple, el equipo de destino en este escenario no es directamente accesible a través de TCP, por lo que Visual Studio proporciona un proxy que expone el protocolo del depurador sobre HTTP. Los proyectos creados con la plantilla web configuran automáticamente este proxy en el archivo *web.debug.config* generado. También se habilita la depuración remota cuando se publica una configuración de **depuración** del proyecto, como se describe en [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

Dado que la depuración remota de Azure usa sockets web, los sockets deben estar habilitados para su instancia de App Service mediante [Azure Portal](https://portal.azure.com); para ello, vaya a **Configuración** > **Configuración de la aplicación** y establezca **Configuración general** > **Sockets web** en **Activado**. Luego, haga clic en **Guardar** para aplicar el cambio. (Tenga en cuenta que la configuración de **Depuración** no se aplica a la depuración de Python).

![Habilitación de sockets web en el portal de Azure](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>Adjuntar con el Explorador de servidores

Una vez que el proyecto está implementado correctamente y están habilitados los sockets web, puede asociarlo a App Service desde el **Explorador de servidores** en Visual Studio (**Ver** > **Explorador de servidores**). Busque el sitio en **Azure** > **App Service** y el grupo de recursos aplicables, haga clic con el botón derecho y seleccione **Asociar depurador (Python)**. (El comando **Asociar depurador** es para aplicaciones .NET que se ejecutan bajo IIS y solo resulta útil si se hospedan de forma conjunta código .NET y la aplicación de Python).

Visual Studio puede llevarle directamente a un conjunto de instrucciones para asociarlo directamente, como se describe a continuación en [Asociar sin el Explorador de servidores](#attach-without-server-explorer). Si no ve el comando **Asociar depurador (Python)** o Visual Studio no puede adjuntarlo al sitio, vea [Solucionador de problemas de depuración remota para Python y Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Si la conexión se realiza correctamente, Visual Studio cambiará a la vista de depurador. La barra de herramientas indica el proceso que se está depurando, como un URI de `wss://`:

![Depuración de un sitio web de Azure App Service](media/azure-remote-debugging-attached.png)

Una vez asociado, la experiencia de depuración es mayormente la misma que para la depuración remota normal sujeta a algunas restricciones. En concreto, el servidor web de IIS que controla las solicitudes entrantes y las delega en el código de Python a través de FastCGI tiene un tiempo de espera de administración de solicitudes, cuyo valor predeterminado es 90 segundos. Si la administración de solicitudes tarda más que el tiempo de expiración (por ejemplo, debido al proceso que se pausa en un punto de interrupción), IIS terminará el proceso, lo que finalizará la sesión de depuración. 

## <a name="attach-without-server-explorer"></a>Asociar sin el Explorador de servidores

Para asociar el depurador directamente a App Service, siga las instrucciones indicadas en la página de información del proxy de WebSocket que Visual Studio implementa en su sitio en *\<site_url>/ptvsd*, como *ptvsdemo.azurewebsites.net/ptvsd*. Al visitar esta página también se comprueba que proxy esté configurado correctamente:

![Página de información del proxy de depuración remota de Azure](media/azure-remote-debugging-proxy-info-page.png)

Como se ha indicado, construya una dirección URL mediante el secreto de *web.debug.config*, que se vuelve a generar cada vez que se publica el proyecto. Este archivo está oculto de forma predeterminada en el **Explorador de soluciones** y no se incluye en el proyecto, por lo que deberá mostrar todos los archivos o abrirlo en un editor distinto. Cuando haya abierto el archivo, mire el valor de appSetting denominado `WSGI_PTVSD_SECRET`:

![Determinación del punto de conexión del depurador en una instancia de Azure App Service](media/azure-remote-debugging-secret.png)

La URL que necesita ahora está en formato `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`, donde &lt;secret&gt; y &lt;site_name&gt; en la cadena se sustituyen por sus valores específicos.

Para asociar el depurador, seleccione **Depurar** > **Asociar a proceso**, seleccione **Depuración remota de Python** en la lista desplegable **Transporte**, y escriba la dirección URL en el **cuadro de texto Calificador**. Luego, presione **Entrar**. Si Visual Studio puede conectarse a App Service, muestra un único proceso de Python en la lista. Selecciónelo y haga clic en **Asociar** para comenzar la depuración:

![Uso del diálogo Asociar a proceso para asociarlo a un sitio web de Azure](media/azure-remote-debugging-manual-attach.png)
