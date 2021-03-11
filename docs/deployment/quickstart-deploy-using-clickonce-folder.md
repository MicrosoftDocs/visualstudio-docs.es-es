---
description: A partir de la versión 16.8 de Visual Studio 2019, puede usar la herramienta Publicar para publicar aplicaciones de escritorio de Windows de .NET Core 3.1 o versiones más recientes con ClickOnce desde Visual Studio.
title: Implementación de una aplicación de escritorio de Windows de .NET con ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165714"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Implementación de una aplicación de escritorio de Windows de .NET con ClickOnce

A partir de la versión 16.8 de Visual Studio 2019, puede usar la herramienta **Publicar** para publicar aplicaciones de escritorio de Windows de .NET Core 3.1 o versiones más recientes con ClickOnce desde Visual Studio.

> [!NOTE]
> Si tiene que publicar una aplicación de escritorio de Windows de .NET Framework, consulte [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic).

## <a name="publishing-with-clickonce"></a>Publicación con ClickOnce

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-clickonce-solution-explorer.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece la página **Publicar**. Seleccione **Nueva**.

1. En el asistente **Publicar**, seleccione **Carpeta**.

    ![Selección de una carpeta como destino de publicación](../deployment/media/quickstart-clickonce-publish-folder-category.png "Elección de carpeta")

1. En la página **Destino específico**, seleccione **ClickOnce**.

    ![Seleccione ClickOnce como destino específico](../deployment/media/quickstart-clickonce-publish-folder-target.png "Elección de ClickOnce")

1. Escriba una ruta de acceso o seleccione **Examinar** para seleccionar la ubicación de publicación.

    ![Especifique la ruta de acceso de la ubicación de publicación](../deployment/media/quickstart-clickonce-publish-location.png "Especificación de una ruta de acceso")

1. En la página **Ubicación de instalación**, seleccione el lugar desde el que los usuarios van a instalar la aplicación.

    ![Especificación de la ruta de acceso a la carpeta](../deployment/media/quickstart-clickonce-install-location.png "Elección de la ubicación de instalación")

1. En la página **Configuración** puede proporcionar la configuración necesaria para ClickOnce.

1. Si seleccionó la instalación desde una ruta de acceso UNC o un sitio web, esta página le permite especificar si la aplicación está disponible sin conexión. Cuando se selecciona esta opción, se muestra la aplicación en el menú Inicio de los usuarios y permite que la aplicación se actualice automáticamente cuando se publica una nueva versión. De forma predeterminada, las actualizaciones están disponibles en la ubicación de instalación.  Si desea usar una ubicación diferente para las actualizaciones, puede especificarla mediante el vínculo Actualizar configuración. Si no desea que la aplicación esté disponible sin conexión, se ejecutará desde la ubicación de instalación.

    ![Especificación de la configuración de publicación](../deployment/media/quickstart-clickonce-unc-settings.png "Elección de la configuración de publicación")

1. Si seleccionó instalar desde un CD, un DVD o una unidad USB, esta página también le permite especificar si la aplicación admite actualizaciones automáticas. Si selecciona la opción para admitir actualizaciones, es necesario especificar la ubicación de la actualización, que debe ser una ruta de acceso UNC o un sitio web válidos.

    ![Elección de la configuración de publicación](../deployment/media/quickstart-clickonce-settings.png "Elección de la configuración de publicación")

En esta página se incluye la capacidad de especificar los **archivos de aplicación** que se van a incluir en la instalación, qué paquetes de **requisitos previos** se van a instalar y otras **opciones** mediante los vínculos que se encuentran en la parte superior de la página.

En esta página también puede establecer la versión de publicación y seleccionar si la versión se incrementará automáticamente con cada publicación.

> [!NOTE]
> El número de versión de publicación es único para cada perfil de ClickOnce. Si planea tener más de un perfil, tendrá que tenerlo en cuenta.

10. En la página **Firmar manifiestos** puede especificar si los manifiestos se deben firmar y qué certificado usar.

    ![Firma de los manifiestos de ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. En la página de **Configuración** puede seleccionar la configuración de proyecto que desee.

     ![Especificación de la configuración de publicación](../deployment/media/quickstart-clickonce-configuration.png)

    Para obtener más ayuda sobre qué configuración elegir, consulte los recursos siguientes:

    - [Implementación dependiente del marco frente a la implementación independiente](/dotnet/core/deploying/)
    - [Identificadores de entorno de ejecución de destino (RID portátil, etc.)](/dotnet/core/rid-catalog)
    - [Configuraciones Debug y Release](../ide/understanding-build-configurations.md)

1. Seleccione **Finalizar** para guardar el nuevo perfil de publicación de ClickOnce.

1. En la página **Resumen**, seleccione **Publicar** y Visual Studio compilará el proyecto y lo publicará en la carpeta de publicación especificada. En esta página también se muestra un resumen del perfil.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-clickonce-summary.png)

1. Para volver a publicar, seleccione **Publicar**.

## <a name="next-steps"></a>Pasos siguientes

Para aplicaciones de .NET:

- [Implementación de .NET Framework y aplicaciones](/dotnet/framework/deployment/)
- [Referencia a ClickOnce](clickonce-reference.md)
