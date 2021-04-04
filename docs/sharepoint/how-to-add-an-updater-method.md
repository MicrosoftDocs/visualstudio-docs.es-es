---
title: 'Cómo: agregar un método Updater | Microsoft Docs'
description: Obtenga información sobre cómo permitir que los usuarios actualicen datos empresariales en una lista externa de SharePoint mediante la adición de un método Updater.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d6337ac237c2a030593b90b29af5e8474052de99
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216740"
---
# <a name="how-to-add-an-updater-method"></a>Cómo: agregar un método Updater
  Puede permitir que los usuarios actualicen datos empresariales en una lista externa de SharePoint mediante la creación de *un método de actualización.* Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Para crear un método Updater

1. En el diseñador de BDC, elija una entidad.

2. En la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC** de Windows.

    Se abre la ventana detalles del método de BDC. Para obtener más información acerca de esta ventana, consulte [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear método de actualización**.

    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana detalles del método de BDC.

   - Un método denominado **Update**.

   - Parámetro de entrada para el método.

   - Descriptor de tipo del parámetro. De forma predeterminada, Visual Studio usa el descriptor de tipo de entidad que definió para el método Finder (por ejemplo: contact).

   - Instancia de método para el método.

     Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Si el identificador del tipo de entidad representa un campo de una tabla de base de datos que no se genera automáticamente, establezca la propiedad de **campo anterior al actualizador** en **true**.

4. En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio que se generó para la entidad y, a continuación, elija **Ver código**.

    El archivo de código de Entity Service se abre en el **Editor de código**. Para obtener más información sobre ese archivo, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Agregue código al método Update para actualizar los datos. En el ejemplo siguiente se actualiza la información de un contacto en la base de datos de ejemplo AdventureWorks para SQL Server.

   > [!NOTE]
   > Reemplace el valor del `ServerName` campo por el nombre del servidor.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet5":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet5":::

## <a name="see-also"></a>Consulte también
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
