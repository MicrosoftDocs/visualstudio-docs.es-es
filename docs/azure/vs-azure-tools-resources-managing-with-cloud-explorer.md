---
title: Administración de recursos de Azure con Cloud Explorer | Microsoft Docs
description: Obtenga más información sobre cómo usar Cloud Explorer para examinar y administrar recursos de Azure en Visual Studio.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 5a69fb83f28f4446a91e4125e75706400401ea1f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911726"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Administración de los recursos asociados con las cuentas de Azure en Cloud Explorer de Visual Studio

Cloud Explorer le permite consultar sus recursos y grupos de recursos de Azure, inspeccionar sus propiedades y realizar acciones de diagnóstico de desarrollador clave desde dentro de Visual Studio.

Del mismo modo que [Azure Portal](https://portal.azure.com), Cloud Explorer se basa en la pila de Azure Resource Manager. Por lo tanto, Cloud Explorer entiende de recursos como, grupos de recursos de Azure, y de servicios de Azure, como aplicaciones lógicas y aplicaciones de API. Además, admite [control de acceso basado en rol](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Requisitos previos

* Visual Studio 2017 o versión posterior (consulte las [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads)) con la **carga de trabajo de Azure** seleccionada. También puede usar una versión anterior de Visual Studio con [Microsoft Azure SDK para .NET 2.9](https://www.microsoft.com/download/details.aspx?id=51657).
* Cuenta de Microsoft Azure: si todavía no tiene ninguna cuenta, puede [registrarse para una evaluación gratuita](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) o [activar las ventajas de suscriptor de Visual Studio](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

> [!NOTE]
> Para ver Cloud Explorer, presione **Ctrl**+**Q** para activar el cuadro de búsqueda y, luego, escriba **Cloud Explorer**.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Incorporación de una cuenta de Azure en Cloud Explorer

Para consultar los recursos asociados con una cuenta de Azure, primero debe agregarla a **Cloud Explorer**.

1. En **Cloud Explorer**, haga clic en el botón **Administración de cuentas**.

   ![Icono de configuración de la cuenta de Azure en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Haga clic en **Administrar cuentas**.

   ![Vínculo para agregar cuenta en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Inicie sesión en la cuenta de Azure cuyos recursos desea examinar.

1. Una vez que inicie sesión en una cuenta de Azure, se muestran las suscripciones asociadas con esa cuenta. Active las casillas de las suscripciones de cuenta que desea examinar y, luego, seleccione **Aplicar**.

   ![Cloud Explorer: seleccione las suscripciones de Azure que se van a mostrar](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Después de seleccionar las suscripciones cuyos recursos desea examinar, tanto las suscripciones como los recursos aparecerán en Cloud Explorer.

   ![Listado de recursos de Cloud Explorer para una cuenta de Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Eliminación de una cuenta de Azure de Cloud Explorer

1. En **Cloud Explorer**, haga clic en **Administración de cuentas**.

   ![Icono de configuración de la cuenta de Azure en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Junto a la cuenta que quiere quitar, haga clic en **Administrar cuenta**.

   ![Icono de configuración de la cuenta de Azure en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Haga clic en **Eliminar** para quitar una cuenta.

    ![Cuadro de diálogo Administrar cuentas de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Vista de tipos de recursos o grupos de recursos

Para ver los recursos de Azure, puede elegir la vista **Tipos de recursos** o **Grupos de recursos**.

1. En **Cloud Explorer**, seleccione la lista desplegable de vistas de recursos.

   ![Lista desplegable de Cloud Explorer para seleccionar la vista de recursos deseada](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. En el menú contextual, seleccione la vista deseada:

   * Vista **Tipos de recursos**: la vista común que se usa en [Azure Portal](https://portal.azure.com). Muestra los recursos de Azure clasificados según su tipo, como aplicaciones web, cuentas de almacenamiento y máquinas virtuales.
   * Vista **Grupos de recursos**: clasifica los recursos de Azure según el grupo de recursos de Azure al que están asociados. Un grupo de recursos es una agrupación de recursos de Azure, normalmente usados por una aplicación específica. Para más información sobre los grupos de recursos de Azure, consulte [Información general de Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   La imagen siguiente muestra una comparación de ambas vistas de recursos:

   ![Comparación de las vistas de recursos de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Visualización y navegación por los recursos en Cloud Explorer

Para navegar a un recurso de Azure y consultar su información en Cloud Explorer, expanda el tipo del elemento o el grupo de recursos asociado y, luego, seleccione el recurso. Cuando selecciona un recurso, aparece información en las dos pestañas, **Acciones** y **Propiedades**, que se encuentran en la parte inferior de Cloud Explorer.

* Pestaña **Acciones**: muestra las acciones que puede realizar en Cloud Explorer con el recurso seleccionado. También puede ver estas opciones si hace clic con el botón derecho en el recurso para ver el menú contextual.

* Pestaña **Propiedades**: muestra las propiedades del recurso, como su tipo, configuración local y grupo de recursos al que está asociado.

La imagen siguiente muestra un ejemplo de comparación de lo que ve en cada pestaña para una instancia de App Service:

  ![Captura de pantalla de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Cada recurso tiene la acción **Abrir en el portal**. Cuando se selecciona esta acción, Cloud Explorer muestra el recurso seleccionado en el [Portal de Azure](https://portal.azure.com). La característica **Abrir en el portal** es especialmente útil para navegar a los recursos profundamente anidados.

También pueden aparecer acciones adicionales y valores de propiedad basados en el recurso de Azure. Por ejemplo, las aplicaciones web y lógicas también tienen las acciones **Abrir en el explorador** y **Adjuntar depurador**, además de **Abrir en el portal**. Cuando se elige un blob, una cola o una tabla de cuenta de almacenamiento, aparecen acciones para abrir editores. Las aplicaciones de Azure tienen las propiedades **URL** y **Status**, mientras que los recursos de almacenamiento tienen propiedades de cadena de conexión y de clave.

## <a name="find-resources-in-cloud-explorer"></a>Búsqueda de recursos en Cloud Explorer

Para buscar recursos con un nombre específico en las suscripciones de cuenta de Azure, escriba el nombre en el cuadro de **búsqueda** en Cloud Explorer.

  ![Buscar recursos en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

A medida que escribe caracteres en el cuadro de **búsqueda**, solo los recursos que coinciden con los caracteres aparecen en el árbol de recursos.
