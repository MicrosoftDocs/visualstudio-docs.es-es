---
title: Agregar una conexión a Azure SQL Database | Microsoft Docs
description: Agregue Azure SQL Database conexión a la aplicación mediante el Servicios conectados de Visual Studio
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9e4a695a26e17e20fbd19081b863d9f108fc16b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841203"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Agregar una conexión a Azure SQL Database

Con Visual Studio, puede conectar cualquiera de los siguientes a Azure SQL Database mediante la característica **servicios conectados** :

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Conexión a Azure SQL Database mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **Azure SQL Database**.

    ![Agregar servicio de Azure SQL Database](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **configurar Azure SQL Database** , seleccione una Azure SQL Database existente y seleccione **siguiente**.

    Si necesita crear un nuevo componente, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Conectar a un componente de Azure SQL Database existente](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Para crear una Azure SQL Database:

   1. Seleccione **crear un SQL Database** en la parte inferior de la pantalla.

   1. Rellene el **Azure SQL Database: crear nueva** pantalla y seleccione **crear**.

       ![Nuevo Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Cuando se muestra la pantalla **configurar Azure SQL Database** , la nueva base de datos aparece en la lista. Seleccione la nueva base de datos en la lista y seleccione **siguiente**.

1. Escriba un nombre de cadena de conexión o elija el valor predeterminado, y elija si desea que la cadena de conexión se almacene en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/azure-sql-database-add-connected-service/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Si se le pide que establezca una regla de firewall, elija **sí**.

   ![Reglas de firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. La conexión aparece en la sección **dependencias de servicio** de la pestaña **servicios conectados** .

   ![Dependencias del servicio](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vea también

- [Azure SQL Database página del producto](https://azure.microsoft.com/services/sql-database/)
- [Documentación de Azure SQL Database](/azure/azure-sql/database/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
