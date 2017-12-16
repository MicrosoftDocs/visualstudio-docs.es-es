---
title: Implementar en una carpeta local - Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8696e7ffb4120bae12538a03b77d62c0d091a7
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Implementar una aplicación web o una aplicación de .NET Core en una carpeta local mediante la herramienta de publicación de Visual Studio

Puede usar el **publicar** herramienta para publicar la aplicación en una carpeta local. 

Estos pasos se aplican a ASP.NET, ASP.NET Core, .NET Core y aplicaciones de Python en Visual Studio. Para Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, elija **archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **.NET Core**y, a continuación, en el panel central, elija **aplicación de consola (.NET Core)**.

1. Escriba un nombre como **MyLocalApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

## <a name="deploy-to-a-local-folder"></a>Implementar en una carpeta local

1. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar**.

    ![Elija publicar](../deployment/media/quickstart-publish.png "elija Publicar")

1. En el **publicar** panel, elija **carpeta**.

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

- [Implementar una aplicación de núcleo de .NET con la herramienta de publicación](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-vs)
- [Empaquetar una aplicación de escritorio de Microsoft Store (puente de escritorio)](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (. NET) [Implementar .NET Framework y aplicaciones](https://docs.microsoft.com/en-us/dotnet/framework/deployment/)
