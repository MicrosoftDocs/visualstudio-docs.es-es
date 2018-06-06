---
title: Implementar en una carpeta local - Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 05/08/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016538bded47a5186294c161cc7f310b26818d15
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764224"
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Implementar una aplicación web o una aplicación de .NET Core en una carpeta local mediante la herramienta de publicación de Visual Studio

Puede usar el **publicar** herramienta para publicar la aplicación en una carpeta local. 

Estos pasos se aplican a ASP.NET, ASP.NET Core, .NET Core y aplicaciones de Python en Visual Studio. Para Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado de Visual Studio 2017 y. **El desarrollo de escritorio NET** carga de trabajo y. **Núcleo de NET** carga de trabajo.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **.NET Core**y, a continuación, en el panel central, elija **aplicación de consola (.NET Core)**.

1. Escriba un nombre como **MyLocalApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

## <a name="deploy-to-a-local-folder"></a>Implementar en una carpeta local

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

    ![Elija publicar](../deployment/media/quickstart-publish.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **carpeta**.

    ![Elija la carpeta](../deployment/media/quickstart-publish-folder.png "Seleccionar carpeta")

1. Escriba una ruta de acceso o haga clic en **examinar** para ir a una carpeta local.

1. Haga clic en **Publicar**.

    Visual Studio compila el proyecto y lo publica en la carpeta especificada.

    El panel de publicación muestra un perfil de resumen.

1. Para configurar opciones de implementación, haga clic en **configuración** en el perfil de resumen.

    ![Configuración de perfil](../deployment/media/quickstart-profile-settings.png "configuración de perfil") 

1. Configurar opciones tales como si se debe implementar una configuración Debug o Release y, a continuación, haga clic en **guardar**.

1. Para volver a publicar, haga clic en **publicar**.

Implemente los archivos publicados de la forma que quiera. Por ejemplo, puede empaquetarlas en un archivo Zip, utilice un comando de copia simple o implementarlas con cualquier paquete de instalación de su elección.

## <a name="next-steps"></a>Pasos siguientes

- [Implementación de una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empaquetado de una aplicación de escritorio para Microsoft Store (Puente de dispositivo de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (. NET) [Implementar .NET Framework y aplicaciones...](/dotnet/framework/deployment/)
