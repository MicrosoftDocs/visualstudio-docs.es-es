---
title: Publicar en un sitio web
ms.date: 06/22/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9744493a8be24ff9ab3e1f8749b02d77d8cc0b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937210"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publique una aplicación web en un sitio web mediante Visual Studio

Puede usar la herramienta **Publicar** para publicar aplicaciones ASP.NET, ASP.NET Core, .NET Core y Python en una sitio web desde Visual Studio. En Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Publicar en un sitio web

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, elija **IIS, FTP, etc.**

    ![Elección de IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "Choose IIS, FTP, etc.")

1. Seleccione **Publicar**. Se abre el cuadro de diálogo de configuración de perfil de publicación.

    ![Selección de Carpeta](../deployment/media/quickstart-publish-settings-web.png "Choose Folder")

1. En el campo **Método de publicación**, elija un método como **Web Deploy** o **FTP**. La configuración que se ve a continuación corresponde al método de publicación. Web Deploy simplifica la implementación de aplicaciones web y sitios web en servidores IIS y debe instalarse como una aplicación en el servidor. Use el [Instalador de plataformaweb](https://www.microsoft.com/web/downloads/platform.aspx) para instalarlo.

1. Configure las opciones necesarias del método de publicación y seleccione **Validar conexión**. Si el servidor o el destino está disponible y la configuración es correcta, aparece un mensaje que indica que la conexión se ha validado y ya está listo para publicar.

    ![Validación de la conexión](../deployment/media/quickstart-publish-web-deploy.png "Validate your connection")

1. Seleccione **Configuración** para configurar otras opciones de implementación, como si se va a implementar una configuración de depuración o versión y seleccione **Guardar**. Si está depurando de forma remota, se requiere una configuración de depuración.

1. Para publicar, seleccione **Publicar**. La ventana de salida muestra el progreso y los resultados de la implementación.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación. También puede configurar un perfil de publicación si importa la configuración de publicación.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en IIS](tutorial-import-publish-settings-iis.md)
