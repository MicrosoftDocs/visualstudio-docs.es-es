---
title: Administrar recursos de Azure con Cloud Explorer | Microsoft Docs
description: Obtenga información sobre cómo usar Cloud Explorer para examinar y administrar recursos de Azure en Visual Studio.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002365"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Administración de los recursos asociados con las cuentas de Azure en Cloud Explorer de Visual Studio

Cloud Explorer le permite ver los grupos de recursos y recursos de Azure, inspeccionar sus propiedades y realizar acciones de diagnóstico de desarrollador clave desde dentro de Visual Studio. 

Al igual que el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer se basa en la pila de Azure Resource Manager. Por lo tanto, Cloud Explorer entiende de recursos como los grupos de recursos de Azure y servicios de Azure como Logic apps y API apps y admite [control de acceso basado en roles](/azure/role-based-access-control/role-assignments-portal.md) (RBAC). 

## <a name="prerequisites"></a>Requisitos previos

* Visual Studio 2015 con el [Microsoft Azure SDK para .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Cuenta de Microsoft Azure: si no tiene una cuenta, puede [registrarse para obtener una evaluación gratuita](http://go.microsoft.com/fwlink/?LinkId=623901) o [activar los beneficios de suscriptor de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Para ver Cloud Explorer, seleccione **vista** > **Cloud Explorer** en la barra de menús.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Agregue una instancia de Azure de la cuenta en Cloud Explorer

Para ver los recursos asociados con una cuenta de Azure, primero debe agregar la cuenta en Cloud Explorer. 

1. En **Cloud Explorer**, seleccione **configuración de la cuenta de Azure**.

   ![Icono de configuración de cuenta de Azure en el explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Seleccione **administrar cuentas**. 

   ![Vínculo de agregar cuenta de explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Inicie sesión en la cuenta de Azure cuyos recursos desea examinar. 

1. Una vez que inicia sesión en una cuenta de Azure, se muestran las suscripciones asociadas con esa cuenta. Active las casillas de las suscripciones de cuenta que desea examinar y, a continuación, seleccione **aplicar**. 

   ![Cloud Explorer: seleccione para mostrar las suscripciones de Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Después de seleccionar las suscripciones cuyos recursos desea examinar, las suscripciones y los recursos se muestran en el explorador en la nube.

   ![Recursos de cloud Explorer lista para una cuenta de Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Quitar una cuenta de Azure de Cloud Explorer 

1. En **Cloud Explorer**, seleccione **administración de cuentas**.

   ![Icono de configuración de cuenta de Azure en el explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Junto a la cuenta que desea quitar, seleccione **administrar cuentas**.

   ![Icono de configuración de cuenta de Azure en el explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Elija **quitar** para quitar una cuenta.

    ![Cuadro de diálogo de cloud Explorer administrar cuentas](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Ver los tipos de recursos o grupos de recursos

Para ver los recursos de Azure, puede elegir **tipos de recursos** o **grupos de recursos** vista.

1. En **Cloud Explorer**, seleccione la lista desplegable de vista de recursos.

   ![Lista de desplegable de cloud Explorer para seleccionar la vista de recursos deseados](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. En el menú contextual, seleccione la vista deseada: 

   * **Tipos de recursos** view - vista común usada en el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), muestra los recursos de Azure clasificados por su tipo, como aplicaciones web, las cuentas de almacenamiento y máquinas virtuales. 
   * **Grupos de recursos** ver - los recursos de Azure se clasifican por el grupo de recursos de Azure con el que está asociados. Un grupo de recursos es una agrupación de recursos de Azure, normalmente usados por una aplicación específica. Para más información acerca de los grupos de recursos de Azure, consulte [información general de Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   La siguiente imagen muestra una comparación de las vistas de dos recursos:

   ![Comparación de las vistas de recursos de explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Ver y navegar por los recursos en Cloud Explorer

Para navegar a un recurso de Azure y ver su información en Cloud Explorer, expanda del elemento tipo o grupo de recursos asociado y, a continuación, seleccione el recurso. Cuando selecciona un recurso, aparece información en las dos pestañas, **acciones** y **propiedades** : en la parte inferior de Cloud Explorer.

* **Acciones** pestaña: muestra las acciones que puede realizar en Cloud Explorer para el recurso seleccionado. También puede ver estas opciones haciendo clic con el recurso para ver el menú contextual.

* **Propiedades** ficha: muestra las propiedades del recurso, como su tipo, configuración regional y grupo de recursos que está asociado.

La siguiente imagen muestra un ejemplo de comparación de lo que ve en cada pestaña para un servicio de aplicación:

  ![Captura de pantalla del explorador en la nube](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Cada recurso tiene la acción **abrir en el portal**. Cuando se selecciona esta acción, Cloud Explorer muestra el recurso seleccionado en el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). El **abrir en el portal** característica es útil para navegar a los recursos profundamente anidados.

Acciones adicionales y los valores de propiedad también pueden aparecer en función de los recursos de Azure. Por ejemplo, web apps y logic apps también tienen las acciones **abrir en el explorador** y **adjuntar depurador** además **abrir en el portal**. Las acciones para abrir editores aparecen cuando se elige un blob de la cuenta de almacenamiento, cola o tabla. Las aplicaciones de Azure tienen **URL** y **estado** propiedades, mientras que los recursos de almacenamiento tienen propiedades de cadena de conexión y la clave.

## <a name="find-resources-in-cloud-explorer"></a>Buscar recursos en Cloud Explorer

Para buscar recursos con un nombre específico en las suscripciones de cuenta de Azure, escriba el nombre de la **búsqueda** cuadro en Cloud Explorer.

  ![Buscar recursos en Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

A medida que escribe caracteres en el **búsqueda** cuadro, solo los recursos que coinciden con los caracteres aparecen en el árbol de recursos.
