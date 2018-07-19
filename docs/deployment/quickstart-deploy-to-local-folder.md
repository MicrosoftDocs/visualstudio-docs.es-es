---
title: Implementar en una carpeta local
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781918"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Implementar una aplicación en una carpeta local con Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones de ASP.NET, ASP.NET Core, .NET Core y Python en una carpeta local desde Visual Studio. Para Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Implementar en una carpeta local

1. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar** (o use el **compilar** > **publicar** elemento de menú).

    ![El comando Publicar en el menú contextual del proyecto en el Explorador de soluciones](../deployment/media/quickstart-publish.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, el **publicar** aparecerá el panel. Seleccione **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **carpeta**.

    ![Elegir una carpeta local como un destino de publicación](../deployment/media/quickstart-publish-folder.png "elegir carpeta")

1. Especifique una ruta de acceso o seleccione **examinar** para especificar una carpeta local.

1. Seleccione **Publicar**. Visual Studio compila el proyecto y lo publica en la carpeta especificada. Las propiedades del proyecto **publicar** aparece el panel, que muestra un perfil de resumen.

    ![Publicar el panel de propiedades que muestra un perfil de resumen](../deployment/media/quickstart-publish-folder-summary.png)

1. Para configurar las opciones de implementación, seleccione **configurar** en el perfil de resumen y seleccione el **configuración** ficha.

    ![Configuración de perfil](../deployment/media/quickstart-profile-settings.png "configuración de perfil")

1. Configurar opciones tales como si se debe implementar una configuración Debug o Release y, a continuación, seleccione **guardar**.

1. Para volver a publicar, seleccione **publicar**.

Implemente los archivos publicados de la forma que quiera. Por ejemplo, puede empaquetarlos en un *.zip* de archivos, use un comando de copia simple o implementarlos con cualquier paquete de instalación de su elección.

## <a name="next-steps"></a>Pasos siguientes

- [Implementación de una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empaquetado de una aplicación de escritorio para Microsoft Store (Puente de dispositivo de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (. NET) [Implementar .NET Framework y aplicaciones](/dotnet/framework/deployment/)
