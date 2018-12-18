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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781918"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Implementar una aplicación en una carpeta local con Visual Studio

Puede usar la herramienta **Publicar** para publicar aplicaciones ASP.NET, ASP.NET Core, .NET Core y Python en una carpeta local desde Visual Studio. En Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Implementar en una carpeta local

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, elija **Carpeta**.

    ![Selección de carpeta local como destino de publicación](../deployment/media/quickstart-publish-folder.png "Selección de carpeta")

1. Especifique una ruta de acceso o seleccione **Examinar** para especificar una carpeta local.

1. Seleccione **Publicar**. Visual Studio compila el proyecto y lo publica en la carpeta especificada. Aparece el panel de propiedades del proyecto **Publicar**, que muestra un resumen de perfil.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-folder-summary.png)

1. Para configurar las opciones de implementación, seleccione **Configurar** en el resumen de perfil y luego la pestaña **Configuración**.

    ![Configuración de perfil](../deployment/media/quickstart-profile-settings.png "Profile settings")

1. Configure opciones como si se va a implementar una configuración de depuración o versión y seleccione **Guardar**.

1. Para volver a publicar, seleccione **Publicar**.

Implemente los archivos publicados de la forma que quiera. Por ejemplo, puede empaquetarlos en un archivo *.zip*, usar un comando de copia simple o implementarlos con el paquete de instalación que prefiera.

## <a name="next-steps"></a>Pasos siguientes

- [Implementación de una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empaquetado de una aplicación de escritorio para Microsoft Store (Puente de dispositivo de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Implementar .NET Framework y aplicaciones](/dotnet/framework/deployment/)
