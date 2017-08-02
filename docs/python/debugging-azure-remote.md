---
title: "Depuración remota de Azure con Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d2caa21359655a2079a853123baea31e471ba040
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="remotely-debugging-python-code-on-azure"></a>Depuración remota de código de Python en Azure

[La compatibilidad con Python en Visual Studio](installation.md) incluye la posibilidad de depurar de forma remota el código de Python que se ejecuta en Azure App Service. A diferencia de la depuración remota simple, la máquina de destino en este escenario no es directamente accesible a través de TCP, por lo que Visual Studio proporciona un proxy que expone el protocolo del depurador sobre HTTP. Los proyectos creados con la plantilla web configuran automáticamente este proxy en el archivo `web.debug.config` generado. También se habilita la depuración remota cuando se publica una configuración de depuración de su proyecto, como se describe en [Publicación en Azure App Service](template-web.md#publishing-to-azure-app-service).

Dado que la depuración remota de Azure usa sockets web, los sockets deben estar habilitados para su instancia de App Service mediante el [portal de Azure](https://portal.azure.com); para ello, vaya a **Configuración > Configuración de la aplicación** y establezca **Configuración general > Sockets web** en **Activado**. Luego, seleccione **Guardar** para aplicar el cambio. (Tenga en cuenta que la configuración de **Depuración** no se aplica a la depuración de Python).

![Habilitación de sockets web en el portal de Azure](~/python/media/azure-remote-debugging-enable-web-sockets.png)

Una vez que el proyecto está implementado correctamente y están habilitados los sockets web, puede asociarlo a App Service desde el **Explorador de servidores** en Visual Studio (**Ver > Explorador de servidores**). Busque el sitio en **Azure > App Service** y el grupo de recursos aplicables, haga clic con el botón derecho y seleccione **Asociar depurador (Python)**. (Tenga en cuenta que el comando **Asociar depurador** es para aplicaciones .NET que se ejecutan bajo IIS y solo es útil si puede hospedar de forma conjunta código .NET y la aplicación de Python).

Visual Studio puede llevarle directamente a un conjunto de instrucciones para asociarlo directamente, como se describe a continuación en [Asociación sin el Explorador de servidores](#attaching-without-server-explorer). Si no ve el comando **Asociar depurador (Python)** o Visual Studio no puede asociarlo a su sitio, consulte [Solución de problemas de depuración remota de Azure](debugging-azure-remote-troubleshooting.md).

Si la asociación es correcta, Visual Studio cambia a la vista de depurador; la barra de herramientas debe indica el proceso que se está depurando como un identificador URI `wss://`:

![Depuración de un sitio web de Azure App Service](~/python/media/azure-remote-debugging-attached.png)

Una vez asociado, la experiencia de depuración es mayormente la misma que para la depuración remota normal sujeta a algunas restricciones. En concreto, el servidor web de IIS que controla las solicitudes entrantes y las delega en el código de Python a través de FastCGI tiene un tiempo de espera de administración de solicitudes, cuyo valor predeterminado es 90 segundos. Si la administración de solicitudes tarda más (por ejemplo, debido al proceso que se pausa en un punto de interrupción), IIS terminará el proceso, que finalizará inmediatamente la sesión de depuración. 

## <a name="attaching-without-server-explorer"></a>Asociación sin el Explorador de servidores

Para asociar el depurador directamente a App Service, siga las instrucciones indicadas en la página de información del proxy de WebSocket que Visual Studio implementa en su sitio en `<site_url>/ptvsd`, como `ptvsdemo.azurewebsites.net/ptvsd`. Al visitar esta página también se comprueba que proxy esté configurado correctamente:

![Página de información del proxy de depuración remota de Azure](~/python/media/azure-remote-debugging-proxy-info-page.png)

Como se ha indicado, deberá construir una dirección URL mediante el secreto de `web.debug.config`, que se vuelve a generar cada vez que se publica el proyecto. Este archivo está oculto de forma predeterminada en el Explorador de soluciones y no se incluye en el proyecto, por lo que deberá mostrar todos los archivos o abrirlo en un editor distinto. Cuando haya abierto el archivo, anote el valor de appSetting denominado `WSGI_PTVSD_SECRET`:

![Determinación del punto de conexión del depurador en una instancia de Azure App Service](~/python/media/azure-remote-debugging-secret.png)

La dirección URL que necesita ahora está en formato `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`, donde &lt;secret&gt; y &lt;site_name&gt; en la cadena se sustituyen desde luego por sus valores específicos.

Para asociar el depurador, seleccione **Depurar > Asociar a proceso**, seleccione **Depuración remota de Python** en la lista desplegable **Transporte**, y escriba la dirección URL en el cuadro de texto **Calificador**. Luego, presione Entrar. Si Visual Studio puede conectarse a App Service, muestra un único proceso de Python en la lista. Selecciónelo y haga clic en **Asociar** para comenzar la depuración:

![Uso del diálogo Asociar a proceso para asociarlo a un sitio web de Azure](~/python/media/azure-remote-debugging-manual-attach.png)

