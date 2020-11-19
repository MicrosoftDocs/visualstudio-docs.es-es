---
title: Agregue Azure CosmosDB mediante Servicios conectados | Microsoft Docs
description: Adición de compatibilidad con CosmosDB de Azure a la aplicación mediante Visual Studio para agregar un servicio conectado
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a2789246a75fe7d2331156eecb106f31f21cbf5
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902927"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Agregue Azure Cosmos DB a la aplicación mediante Visual Studio Servicios conectados

Con Visual Studio, puede conectar cualquiera de las siguientes opciones para Azure Cosmos DB mediante el uso de la característica **servicios conectados** :

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Conexión a Azure Cosmos DB mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **Azure Cosmos dB**.

    ![Agregar Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **Azure Cosmos dB** , seleccione una Azure Cosmos dB existente y seleccione **siguiente**.

    Si tiene que crear una base de datos, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Agregar Cosmos DB existentes al proyecto](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Para crear una Azure Cosmos DB:

   1. Seleccione **crear un nuevo Azure Cosmos dB** en la parte inferior de la pantalla.

   1. Rellene el **Azure Cosmos dB: crear nueva** pantalla y seleccione **crear**.

       ![Nuevo Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Cuando se muestra el cuadro de diálogo **configurar Azure Cosmos dB** , la nueva base de datos aparece en la lista. Seleccione la nueva base de datos en la lista y seleccione **siguiente**.

1. Escriba un nombre de cadena de conexión y elija si desea almacenar la cadena de conexión en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. La conexión aparece en la sección **dependencias de servicio** de la pestaña **servicios conectados** .

   ![Dependencias del servicio](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Consulte también

- [Azure Cosmos DB página del producto](https://azure.microsoft.com/services/cosmos-db/)
- [Documentación sobre Azure Cosmos DB](/azure/cosmos-db/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
