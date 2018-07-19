---
title: Publicar en un sitio Web
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077508"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publicar una aplicación Web en un sitio web mediante Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones de ASP.NET, ASP.NET Core, .NET Core y Python en un sitio Web desde Visual Studio. Para Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Publicar en un sitio Web

1. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar** (o use el **compilar** > **publicar** elemento de menú).

    ![El comando Publicar en el menú contextual del proyecto en el Explorador de soluciones](../deployment/media/quickstart-publish.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, el **publicar** aparecerá el panel. Seleccione **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **IIS, FTP, etcetera**.

    ![Elija IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "elija IIS, FTP, etcetera.")

1. Seleccione **Publicar**. El perfil de publicación abrirá el cuadro de diálogo de configuración.

    ![Elija la carpeta](../deployment/media/quickstart-publish-settings-web.png "elegir carpeta")

1. En el **método Publish** , a continuación, elija un método como **Web Deploy** o **FTP**. La configuración que se ve a continuación se corresponde con el método de publicación. Web Deploy simplifica la implementación de aplicaciones Web y sitios Web en servidores de IIS y debe instalarse como una aplicación en el servidor. Use la [instalador de plataforma Web](https://www.microsoft.com/web/downloads/platform.aspx) para instalarlo.

1. Configure las opciones necesarias para el método de publicación y seleccione **validar conexión**. Si el servidor o el destino está disponible y la configuración es correcta, se valida un mensaje que indica la conexión, y está listo para publicar.

    ![Validar la conexión](../deployment/media/quickstart-publish-web-deploy.png "validar la conexión")

1. Seleccione **configuración** para configurar otras opciones de implementación, por ejemplo, si desea implementar una configuración Debug o Release y, a continuación, seleccione **guardar**. Si está depurando de forma remota, se requiere una configuración de depuración.

1. Para publicar, seleccione **publicar**. La ventana de salida muestra los resultados y el progreso de la implementación.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a usar Visual Studio para crear un perfil de publicación. También puede configurar la publicación de una perfil mediante la importación de la configuración de publicación.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en IIS](tutorial-import-publish-settings-iis.md)
