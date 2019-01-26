---
title: Procedimiento Agregar un método Deleter | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: cad4de5ed1b31d02d9136b5ec2b46be71f54fea4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870888"
---
# <a name="how-to-add-a-deleter-method"></a>Procedimiento Agregar un método Deleter
  Puede habilitar un usuario final eliminar un registro de datos de una lista externa en un sitio de SharePoint mediante la adición de un método Deleter al modelo. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Para crear un método Deleter  
  
1. En el **Diseñador de BDC**, elegir una entidad.  
  
2. En la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC**.  
  
    El **detalles del método de BDC** abre la ventana. Para obtener más información acerca de esta ventana, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. En el **agregue un método** elija **crear un método Deleter**.  
  
    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la **detalles del método de BDC** ventana.  
  
   - Un método denominado **eliminar**.  
  
   - Un parámetro de entrada para el método.  
  
   - Un descriptor de tipos para el parámetro.  
  
   - Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
    El archivo de código del servicio de entidad se abre en el Editor de código. Para obtener más información sobre el archivo de código del servicio de entidad, vea [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Agregue código al método Deleter para eliminar un registro. El ejemplo siguiente elimina un elemento de línea de un pedido de venta mediante el uso de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
   > [!NOTE]  
   >  El método en este ejemplo utiliza dos parámetros de entrada.  
  
   > [!NOTE]  
   >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Vea también
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)  
