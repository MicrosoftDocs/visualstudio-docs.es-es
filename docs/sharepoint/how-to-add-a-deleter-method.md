---
title: 'Cómo: agregar un método de eliminación | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd97d28936e9f0cc50e9064fdc1a6a64bb20fc77
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017040"
---
# <a name="how-to-add-a-deleter-method"></a>Cómo: agregar un método de eliminación
  Puede permitir que un usuario final elimine un registro de datos de una lista externa en un sitio de SharePoint agregando un método de eliminación al modelo. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Para crear un método de eliminación

1. En el **Diseñador de BDC**, elija una entidad.

2. En la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC**de Windows.

    Se abre la ventana **detalles del método de BDC** . Para obtener más información acerca de esta ventana, consulte [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear un método de eliminación**.

    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana **detalles del método de BDC** .

   - Un método denominado **Delete**.

   - Parámetro de entrada para el método.

   - Descriptor de tipo del parámetro.

   - Instancia de método para el método.

     Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

4. En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio que se generó para la entidad y, a continuación, elija **Ver código**.

    El archivo de código de Entity Service se abre en el editor de código. Para obtener más información sobre el archivo de código de Entity Service, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Agregue código al método eliminador para eliminar un registro. En el ejemplo siguiente se elimina un elemento de línea de un pedido de ventas mediante la base de datos de ejemplo AdventureWorks para SQL Server.

   > [!NOTE]
   > El método en este ejemplo utiliza dos parámetros de entrada.

   > [!NOTE]
   > Reemplace el valor del `ServerName` campo por el nombre del servidor.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>Consulte también
- [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
