---
title: Adición de Azure Storage con Servicios conectados | Microsoft Docs
description: Agregue una dependencia del servicio Azure Storage a la aplicación mediante el Servicios conectados de Visual Studio
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: d169940d6deffdf67bcbcb94e9f647631d0f606a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902641"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Adición de almacenamiento de Azure mediante Servicios conectados de Visual Studio

Con Visual Studio, puede conectar cualquiera de las siguientes opciones para Azure Storage mediante el uso de la característica **servicios conectados** :

- Aplicación de consola de .NET Framework
- ASP.NET MVC (.NET Framework)
- ASP.NET Core
- .NET Core (incluida la aplicación de consola, WPF, Windows Forms, biblioteca de clases)
- Rol de trabajo de .NET Core
- Azure Functions
- Plataforma universal de Windows aplicación
- Xamarin
- Cordova

La funcionalidad del servicio conectado agrega todo el código de conexión y las referencias necesarios al proyecto y modifica los archivos de configuración de forma adecuada.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En Visual Studio para Mac, vea [Servicios conectados en Visual Studio para Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Requisitos previos

- Visual Studio con la carga de trabajo de Azure instalada.
- Proyecto de uno de los tipos admitidos

## <a name="connect-to-azure-storage-using-connected-services"></a>Conexión a Azure Storage mediante Servicios conectados

::: moniker range="vs-2017"

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

    ![Incorporación de un servicio conectado de Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. En la página **Servicios conectados**, seleccione **Almacenamiento en la nube con Azure Storage**.

    ![Incorporación de Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. En el cuadro de diálogo **Azure Storage**, elija una cuenta de almacenamiento existente y seleccione **Agregar**.

    Si necesita crear una cuenta de almacenamiento, vaya al siguiente paso. De lo contrario, vaya al paso 6.

    ![Incorporación de una cuenta de almacenamiento existente al proyecto](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Para crear una cuenta de almacenamiento:

   1. Seleccione **Crear una nueva cuenta de almacenamiento** en la parte inferior del cuadro de diálogo.

   1. Rellene el cuadro de diálogo **Crear cuenta de almacenamiento** y seleccione **Crear**.

       ![Nueva cuenta de almacenamiento de Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Cuando se muestre el cuadro de diálogo **Azure Storage**, la nueva cuenta de almacenamiento aparecerá en la lista. Seleccione la nueva cuenta de almacenamiento en la lista y seleccione **Agregar**.

1. El servicio de almacenamiento conectado aparece bajo el nodo **Referencias de servicio** del proyecto.
:::moniker-end

:::moniker range=">=vs-2019"

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

    ![Incorporación de un servicio conectado de Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **Azure Storage**.

    ![Incorporación de Azure Storage](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **configurar Azure Storage** , seleccione una cuenta de almacenamiento existente y seleccione **siguiente**.

    Si necesita crear una cuenta de almacenamiento, vaya al siguiente paso. De lo contrario, vaya al paso 6.

    ![Incorporación de una cuenta de almacenamiento existente al proyecto](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Para crear una cuenta de almacenamiento:

   1. Seleccione **crear una cuenta de almacenamiento** en la parte inferior del cuadro de diálogo.

   1. Rellene el cuadro de diálogo **Azure Storage: crear nuevo** y seleccione **crear**.

       ![Nueva cuenta de almacenamiento de Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Cuando se muestre el cuadro de diálogo **Azure Storage**, la nueva cuenta de almacenamiento aparecerá en la lista. Seleccione la nueva cuenta de almacenamiento en la lista y seleccione **siguiente**.

1. Escriba un nombre de cadena de conexión y elija si desea almacenar la cadena de conexión en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. El servicio de almacenamiento conectado aparece bajo el nodo **Referencias de servicio** del proyecto.
:::moniker-end

## <a name="see-also"></a>Consulte también

- [Foro de Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Documentación de Azure Storage](/azure/storage/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
