---
title: Agregar una conexión a Azure SQL Database | Microsoft Docs
description: Agregue Azure SQL Database conexión a la aplicación mediante el Visual Studio Servicios conectados
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 26a01bfe2a34422f9596710f832a1c4af699fd3b
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588493"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Agregar una conexión a Azure SQL Database

Con Visual Studio, puede conectar cualquiera de las siguientes Azure SQL Database mediante la **característica Servicios conectados** siguiente:

- .NET Framework aplicación de consola
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (incluida la aplicación de consola, WPF, Windows Forms, biblioteca de clases)
- Rol de trabajo de .NET Core
- Azure Functions
- Plataforma universal de Windows app
- Xamarin
- Cordova

La funcionalidad del servicio conectado agrega todo el código de conexión y las referencias necesarios al proyecto y modifica los archivos de configuración de forma adecuada.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En Visual Studio para Mac, vea [Servicios conectados en Visual Studio para Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Requisitos previos

- Visual Studio con la carga de trabajo de Azure instalada.
- Un proyecto de uno de los tipos admitidos

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Conexión a Azure SQL Database mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el **botón derecho en Servicios conectados** nodo y, en el menú contextual, seleccione Agregar servicio **conectado.**

1. En la **Servicios conectados,** seleccione el icono + de **Dependencias de servicio.**

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la **página Agregar** dependencia, **seleccione Azure SQL Database**.

    ![Agregar Azure SQL Database Service](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la **pantalla Configurar Azure SQL Database,** seleccione un Azure SQL Database existente y seleccione **Siguiente.**

    Si necesita crear un nuevo componente, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Conexión al componente Azure SQL Database existente](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Para crear una Azure SQL Database:

   1. Seleccione **Crear un SQL Database** en la parte inferior de la pantalla.

   1. Rellene la **Azure SQL Database: Crear nueva** pantalla y seleccione **Crear**.

       ![Nuevo Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Cuando se **muestra la Azure SQL Database** configuración, la nueva base de datos aparece en la lista. Seleccione la nueva base de datos en la lista y seleccione **Siguiente.**

1. Escriba un nombre de cadena de conexión o elija el valor predeterminado y elija si desea que la cadena de conexión se almacene en un archivo de secretos local o en [Azure Key Vault](/azure/key-vault).

   ![Especificación de la cadena de conexión](./media/azure-sql-database-add-connected-service/connection-string.png)

1. La **pantalla Resumen de cambios** muestra todas las modificaciones que se realizarán en el proyecto si completa el proceso. Si los cambios parecen correctos, elija **Finalizar.**

   ![Resumen de cambios](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Si se le pide que establezca reglas de firewall, elija **Sí.**

   ![Reglas de firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. La conexión aparece en la **sección Dependencias del** servicio **de** Servicios conectados pestaña.

   ![Dependencias del servicio](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vea también

- [Azure SQL Database página del producto](https://azure.microsoft.com/services/sql-database/)
- [Documentación de Azure SQL Database](/azure/azure-sql/database/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
