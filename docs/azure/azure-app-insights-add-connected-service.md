---
title: Agregue Aplicación de Azure Insights mediante Servicios conectados | Microsoft Docs
description: Agregar Aplicación de Azure información a la aplicación mediante el uso de Visual Studio para agregar un servicio conectado
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643292"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Agregue Aplicación de Azure Insights mediante Visual Studio Servicios conectados

Con Visual Studio, puede conectar cualquiera de las siguientes opciones para Aplicación de Azure información mediante la característica de **servicios conectados** :

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

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Conéctese a Aplicación de Azure Insights mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **aplicación de Azure Insights**.

    ![Agregar Aplicación de Azure Insights](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **configurar aplicación de Azure Insights** , seleccione un componente de aplicación de Azure Insights existente y seleccione **siguiente**.

    Si necesita crear un nuevo componente, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Conectar a un componente de Application Insights existente](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Para crear un componente de Application Insights:

   1. Seleccione **crear un nuevo Application Insights componente** en la parte inferior de la pantalla.

   1. Rellene el **Application Insights: crear nueva** pantalla y seleccione **crear**.

       ![Nuevo componente de App de Azure Insights](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Cuando se muestra la pantalla **configurar aplicación de Azure Insights** , el nuevo componente aparece en la lista. Seleccione el nuevo componente en la lista y seleccione **siguiente**.

1. Escriba un nombre de clave de instrumentación o elija el valor predeterminado, y elija si desea que la cadena de conexión se almacene en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/azure-app-insights-add-connected-service/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. La conexión aparece en la sección **dependencias de servicio** de la pestaña **servicios conectados** .

   ![Dependencias del servicio](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Consulte también

- [Azure Monitor página del producto](https://azure.microsoft.com/services/monitor/)
- [Documentación de App de Azure Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
