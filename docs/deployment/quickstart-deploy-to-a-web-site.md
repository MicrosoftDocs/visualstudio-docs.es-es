---
title: Publicar en un sitio Web - Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b6bacc45d78d1d246f6a91d13549ccc96b276a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publicar una aplicación web o una aplicación de .NET Core en un sitio web mediante la herramienta de publicación de Visual Studio

Puede usar el **publicar** herramienta para publicar las aplicaciones ASP.NET en un sitio Web.

Estos pasos se aplican a ASP.NET, ASP.NET Core, .NET Core y aplicaciones de Python en Visual Studio. Para Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central elija **aplicación Web de ASP.NET (.NET Framework)**(solo C#) o **aplicación Web de ASP.NET Core**y, a continuación, haga clic en **Aceptar**.

1. Elija **MVC**, asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **generar > compilar solución** para compilar el proyecto.

## <a name="publish-to-a-web-site"></a>Publicar en un sitio web

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

    ![Elija publicar](../deployment/media/quickstart-publish-aspnet.png "elija Publicar")

1. En el **publicar** panel, elija **IIS, FTP, etcetera**.

    ![Elija IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "elegir IIS, FTP, etcetera.")

1. Haga clic en **Publicar**.

    El perfil de configuración que se abre el cuadro de diálogo de publicación.

    ![Elija la carpeta](../deployment/media/quickstart-publish-settings-web.png "Seleccionar carpeta")

1. En el **método de publicación** , a continuación, elija un método como **Web Deploy** o **FTP**.

    Las opciones que se ven a continuación corresponden al método de publicación.

1. Configurar los valores obligatorios para el método de publicación y haga clic en **validar conexión**.

    Si el servidor o el destino está disponible y la configuración es correcta, verá un mensaje que indica la conexión se valida y esté listo para publicar.

    ![Validar la conexión](../deployment/media/quickstart-publish-web-deploy.png "validar la conexión")

1. Si desea configurar otras opciones de implementación, haga clic en **configuración**.

    Puede configurar opciones como la posibilidad de implementar una configuración Debug o Release y, a continuación, haga clic en **guardar**. Si depura de forma remota, se requiere una configuración de depuración.

1. Para publicar, haga clic en **publicar**.

    La ventana de resultados muestra los resultados y el progreso de la implementación.

## <a name="next-steps"></a>Pasos siguientes

- [Implementación de ASP.NET en IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
