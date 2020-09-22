---
title: Implementar en una carpeta local
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 800059dc8d5a3e6ccfb72c588fbb61423a338cba
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036397"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Implementación de una aplicación en una carpeta con Visual Studio

Puede usar la herramienta **Publicar** para publicar aplicaciones ASP.NET, ASP.NET Core, .NET Core y Python en una carpeta desde Visual Studio. En Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si tiene que publicar una aplicación de escritorio de Windows en una carpeta, consulte [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic). Para C++ y CLR, vea [Implementación de ClickOnce para aplicaciones de Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), o bien, para C y C ++, vea [Implementación de una aplicación de Visual C++ mediante un proyecto de instalación](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Implementar en una carpeta local

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece la ventana **Publicar**. Seleccione **Nuevo**.

1. En la ventana **Publicar**, seleccione **Carpeta**.

    ![Selección de una carpeta como destino de publicación](../deployment/media/quickstart-publish-folder-new.png "Elección de carpeta")

1. Especifique una ruta de acceso o seleccione **Examinar** para especificar una carpeta.

    ![Especificación de la ruta de acceso a la carpeta](../deployment/media/quickstart-publish-folder-path.png "Elección de carpeta")

1. Seleccione **Publicar**. Visual Studio compila el proyecto y lo publica en la carpeta especificada. Aparece el panel de propiedades del proyecto **Publicar**, que muestra un resumen de perfil.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-folder-summary.png)

1. Para configurar las opciones de implementación, seleccione **Editar** en el resumen de perfil y elija la pestaña **Configuración**.

   La configuración que ve depende del tipo de aplicación. En la ilustración siguiente se muestra una configuración de ejemplo para una aplicación de ASP.NET Core.

    ![Configuración del perfil](../deployment/media/quickstart-profile-settings.png "Configuración del perfil")

    Para más ayuda sobre cómo elegir la configuración en .NET, consulte los recursos siguientes:

    - [Implementación dependiente del marco frente a la implementación independiente](/dotnet/core/deploying/)
    - [Identificadores de entorno de ejecución de destino (RID portátil, etc.)](/dotnet/core/rid-catalog)
    - [Configuraciones Debug y Release](../ide/understanding-build-configurations.md)

1. Configure opciones como si se va a implementar una configuración de depuración o versión y seleccione **Guardar**.

1. Para volver a publicar, seleccione **Publicar**.

Implemente los archivos publicados de la forma que quiera. Por ejemplo, puede empaquetarlos en un archivo *.zip*, usar un comando de copia simple o implementarlos con el paquete de instalación que prefiera.

## <a name="next-steps"></a>Pasos siguientes

Para aplicaciones de .NET:

- [Implementación de una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs)
- [Publicación de aplicaciones de .NET Core (implementación dependiente del marco frente a la implementación independiente)](/dotnet/core/deploying/)
- [Implementación de .NET Framework y aplicaciones](/dotnet/framework/deployment/)
