---
title: Procedimiento Agregar un método Creator | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fe40d6f8b5032dbbffeeda3edaff3b1c89aadb3f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867161"
---
# <a name="how-to-add-a-creator-method"></a>Procedimiento Agregar un método Creator
  Un método Creator agrega nuevos datos al origen de datos de una entidad. El servicio de conectividad de datos profesionales (BDC) llama a este método cuando los usuarios elijan el **nuevo elemento** situado en la **cinta** de una lista que se basa en el modelo. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Para agregar un método Creator  
  
1. En el **Diseñador de BDC**, elegir una entidad.  
  
2. En la barra de menús, elija **vista** > **Other Windows** >**detalles del método de BDC**.  
  
    El **detalles del método de BDC** abre la ventana. Para obtener más información acerca de esta ventana, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. En el **agregue un método** elija **crear método Creator**.  
  
    Visual Studio agrega los siguientes elementos al modelo, y estos elementos aparecen en la **detalles del método de BDC** ventana.  
  
   - Un método denominado **crear**.  
  
   - Un parámetro de entrada para el método.  
  
   - Un parámetro de valor devuelto del método.  
  
   - Descriptores para los parámetros de tipo.  
  
   - Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
    El archivo de código del servicio de entidad se abre en el Editor de código. Para obtener más información sobre el archivo de código del servicio de entidad, vea [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Agregue código al método Creator que agrega datos al origen de datos. En el ejemplo siguiente se agrega un contacto a la base de datos de ejemplo AdventureWorks para SQL Server.  
  
   > [!NOTE]  
   >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Vea también
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)  
