---
title: Agregue caché de Azure para Redis mediante Servicios conectados | Microsoft Docs
description: Adición de caché de Azure para la compatibilidad de Redis con la aplicación mediante Visual Studio para agregar un servicio conectado
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 7583848c4bbe38f9094c60998e16ca3e95cf399f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643280"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Agregue caché de Azure para Redis mediante Visual Studio Servicios conectados

Con Visual Studio, puede conectar cualquiera de las siguientes a la caché de Azure para Redis mediante la característica **servicios conectados** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Conexión a la caché de Azure para Redis con Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **caché de Azure para Redis**.

    ![Adición de Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/account/free).

1. En la pantalla **configurar caché de Azure para Redis** , seleccione una caché de Azure existente para Redis y seleccione **siguiente**.

    Si necesita crear un nuevo componente, vaya al paso siguiente. De lo contrario, vaya al paso 7.

    ![Conexión a la caché de Azure existente para Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Para crear una Azure Redis Cache:

   1. Seleccione **crear un nuevo Azure Redis cache** en la parte inferior de la pantalla.

   1. Rellene la **memoria caché de Azure para Redis: crear nueva** pantalla y seleccione **crear**.

       ![Nueva caché de Azure para Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Cuando se muestra la pantalla **configurar caché de Azure para Redis** , la nueva memoria caché aparece en la lista. Seleccione la nueva base de datos en la lista y seleccione **siguiente**.

1. Escriba un nombre de cadena de conexión o elija el valor predeterminado, y elija si desea que la cadena de conexión se almacene en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. La conexión aparece en la sección **dependencias de servicio** de la pestaña **servicios conectados** .

   ![Dependencias del servicio](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Consulte también

- [Página del producto caché de Azure para Redis](https://azure.microsoft.com/services/cache)
- [Documentación de Azure Cache for Redis](/azure/azure-cache-for-redis/)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)