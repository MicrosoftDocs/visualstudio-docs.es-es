---
title: Agregar App de Azure configuración mediante Servicios conectados | Microsoft Docs
description: Agregue una dependencia del servicio de configuración de Azure a la aplicación mediante el Servicios conectados de Visual Studio
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727299"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Agregar App de Azure configuración mediante Visual Studio Servicios conectados

En este tutorial, aprenderá a agregar fácilmente todo lo que necesita para empezar a usar App de Azure configuración para administrar la configuración y las marcas de características para proyectos web en Visual Studio, independientemente de que use ASP.NET Core o cualquier tipo de proyecto ASP.NET. Mediante el uso de la característica Servicios conectados de Visual Studio, puede hacer que Visual Studio agregue automáticamente todo el código, los paquetes NuGet y los valores de configuración que necesita para conectarse al recurso de configuración de la aplicación en Azure. Para usar esta característica, debe usar Visual Studio 2019 versión 16,9 o posterior.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En Visual Studio para Mac, vea [Servicios conectados en Visual Studio para Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Prerrequisitos

- Visual Studio con la carga de trabajo de Azure instalada.
- Proyecto de uno de los tipos admitidos

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Conexión a la configuración de App de Azure mediante Servicios conectados

1. Abra el proyecto en Visual Studio.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **servicios conectados** y, en el menú contextual, seleccione **Agregar servicio conectado**.

    ![Incorporación de un servicio conectado de Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. En la pestaña **servicios conectados** , seleccione el icono + para las **dependencias de servicio**.

    ![Agregar dependencia de servicio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. En la página **Agregar dependencia** , seleccione **App de Azure configuración**.

    ![Agregar configuración de aplicaciones](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Si aún no ha iniciado sesión, inicie sesión en su cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/free/dotnet).

1. En la pantalla **configurar App de Azure configuración** , seleccione la suscripción y un almacén de configuración existente. Luego, seleccione **Siguiente**.

    Si necesita crear un almacén de configuración de la aplicación, vaya al paso siguiente. De lo contrario, vaya al paso 6.

    ![Agregar cuenta de configuración existente al proyecto](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Para crear un almacén de configuración de la aplicación:

   1. Seleccione el icono + situado a la derecha del encabezado **almacenes de configuración** de la aplicación. 

   1. Rellene el cuadro de diálogo **configuración de App de Azure: crear nuevo** y seleccione **crear**. Tenga en cuenta que el campo Nombre del recurso debe ser único. 

       ![Nuevo almacén de configuración de aplicaciones de Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Cuando se muestra el cuadro de diálogo **configuración de App de Azure** , el nuevo almacén de configuración aparece en la lista. Seleccione este nuevo almacén y, a continuación, seleccione **siguiente**.

1. Escriba un nombre de cadena de conexión y elija si desea almacenar la cadena de conexión en un archivo de secretos locales o en [Azure Key Vault](/azure/key-vault).

   ![Especificar cadena de conexión](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. En la pantalla **Resumen de cambios** se muestran todas las modificaciones que se realizarán en el proyecto si se completa el proceso. Si los cambios son correctos, elija **Finalizar**.

   ![Resumen de cambios](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Una vez finalizado el **proceso de configuración de dependencia** , App de Azure configuración aparece ahora en el nodo **dependencias de servicio** del proyecto.

## <a name="next-steps"></a>Pasos siguientes

Más información sobre la configuración de App de Azure en la [documentación de configuración de App de Azure](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Consulte también

- [Tutorial para usar la configuración dinámica en una configuración de aplicación conectada ASP.NET Core aplicación](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Servicios conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)