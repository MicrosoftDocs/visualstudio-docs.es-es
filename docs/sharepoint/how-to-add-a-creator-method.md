---
title: "Cómo: agregar un método Creator | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 354d3f574515fcc9e8417e817363f9bbe7327f06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-creator-method"></a>Cómo: Agregar un método Creator
  Un método Creator agrega nuevos datos al origen de datos de una entidad. El servicio de conectividad de datos profesionales (BDC) llama a este método cuando los usuarios eligen el **nuevo elemento** botón en la cinta de opciones de una lista que se basa en el modelo. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Para agregar un método Creator  
  
1.  En el Diseñador de BDC, elija una entidad.  
  
2.  En la barra de menús, elija **vista**, **otras ventanas**, **detalles del método de BDC**.  
  
     El **detalles del método de BDC** abre la ventana. Para obtener más información acerca de esta ventana, consulte [herramientas información general del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En el **agregar un método** elija **crear método Creator**.  
  
     Visual Studio agrega los siguientes elementos al modelo, y estos elementos aparecen en la **detalles del método de BDC** ventana.  
  
    -   Un método denominado **crear**.  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un parámetro de valor devuelto del método.  
  
    -   Descriptores de los parámetros de tipo.  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
     El archivo de código del servicio de entidad se abre en el Editor de código. Para obtener más información sobre el archivo de código del servicio de entidad, vea [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Agregue código al método Creator que agrega datos al origen de datos. En el ejemplo siguiente se agrega un contacto a la base de datos de ejemplo de AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Sustituya el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Vea también  
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  