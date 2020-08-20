---
title: Agregue Azure Signalr mediante Servicios conectados | Microsoft Docs
description: Agregar Azure Signalr a la aplicación mediante el uso de Visual Studio para agregar un servicio conectado
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0e44416bd6a55796b62a7590856caab8466a6401
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643251"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Agregar Azure Signalr mediante Visual Studio Servicios conectados

Con Visual Studio, puede conectar cualquiera de los siguientes a Azure Signalr Service mediante la característica **servicios conectados** :

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
## <a name="prerequisites"></a>Prerrequisitos

- Visual Studio con la carga de trabajo de Azure instalada.
- Proyecto de uno de los tipos admitidos

## <a name="connect-to-azure-signalr-using-connected-services"></a>Conexión a Azure Signalr mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **Azure signalr Service**.

    ![Incorporación del servicio Azure Signalr](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **configurar Azure signalr** , seleccione un componente de Azure signalr existente y seleccione **siguiente**.

    Si necesita crear un nuevo componente, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Conexión a un componente existente de Azure Signalr](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Para crear una instancia de Azure Signalr Service:

   1. Seleccione **crear una nueva instancia de Azure signalr Service** en la parte inferior de la pantalla.

   1. Rellene el **servicio Azure signalr: crear nueva** pantalla y seleccione **crear**.

       ![Nueva instancia de servicio de Azure Signalr](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Cuando se muestra la pantalla **configurar el servicio Azure signalr** , la nueva instancia aparece en la lista. Seleccione la nueva instancia en la lista y, a **continuación**, seleccione siguiente.

1. Escriba un nombre de cadena de conexión o elija el valor predeterminado, y elija si desea que la cadena de conexión se almacene en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/azure-signalr-add-connected-service/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. La conexión aparece en la sección **dependencias de servicio** de la pestaña **servicios conectados** .

   ![Dependencias del servicio](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Consulte también

- [Página de producto de Azure Signalr](https://azure.microsoft.com/services/signalr-service/)
- [Documentación de Azure SignalR Service](/azure/azure-signalr)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
