---
title: "Crear características de SharePoint | Documentos de Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
ms.assetid: 2e211fb3-94f4-4921-ba77-2ba6717a3e41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8f78a12aa70c3c7042a821a737485da963f7a56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-features"></a>Crear características de SharePoint
  Puede usar una característica de SharePoint para agrupar elementos relacionados de proyecto de SharePoint para una implementación más sencilla. Puede crear características, establecer ámbitos y marcar otras características como dependencias utilizando el Diseñador de características de SharePoint. El diseñador también genera un manifiesto, que es un archivo XML que describe cada característica.  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>Agregar características a la solución de SharePoint  
 Puede agregar una característica a la solución de SharePoint mediante el Explorador de soluciones o el Explorador de empaquetado. Puede usar uno de los métodos siguientes para agregar una característica.  
  
-   En **el Explorador de soluciones**, abra el menú contextual para **características**y, a continuación, elija **Agregar característica**.  
  
-   En **Explorador de empaquetado**, abra el menú contextual para el paquete y, a continuación, elija **Agregar característica**.  
  
## <a name="using-the-feature-designer"></a>Utilizando el Diseñador de características  
 Una solución de SharePoint puede contener una o más características de SharePoint, que se agrupan bajo el nodo de la característica en el Explorador de soluciones. Cada característica tiene su propio **Diseñador de características** que puede usar para personalizar las propiedades de características. Para obtener más información, consulte [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Para distinguir las características de otros, puede configurar las propiedades de características como el título, la descripción, la versión y el ámbito.  
  
### <a name="feature-designer-options"></a>Opciones del Diseñador de características  
 Después de crear una característica, puede utilizar el Diseñador de características para personalizarlo.  
  
 La tabla siguiente describen las propiedades de características que se muestran en el Diseñador de características.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Título|Opcional. El título predeterminado de la característica está establecido en *nombresolución**NombreCaracterística*.|  
|Descripción|Opcional. La descripción de la característica de SharePoint.|  
|Ámbito|Obligatorio. Si una característica se crea mediante el uso de **el Explorador de soluciones**, el ámbito está establecido en Web de forma predeterminada.<br /><br /> -Granja: Activar una característica para una granja de servidores completa.<br /><br /> -Sitio: Activar una característica para todos los sitios web en una colección de sitios.<br /><br /> -Web: Activar una característica para un sitio web específico.<br /><br /> -WebApplication: Activar una característica para todos los sitios web en una aplicación web.|  
|Elementos de la solución|Todos los elementos de SharePoint que se pueden agregar a la característica.|  
|Elementos de la característica|Los elementos de proyecto de SharePoint que se han agregado a la característica.|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>Agregar y quitar elementos de proyecto de SharePoint  
 Puede seleccionar qué elementos de proyecto de SharePoint que desea agregar una característica de SharePoint para la implementación. Use la **Diseñador de características** para agregar y quitar elementos de características y ver el manifiesto de la característica. Para obtener más información, consulte [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="adding-feature-dependencies"></a>Agregar dependencias de características  
 Puede configurar el manifiesto de la característica para que el servidor de SharePoint Active algunas características antes de que la característica está activada. Por ejemplo, si la característica de SharePoint depende de otras características para la funcionalidad o datos, el servidor de SharePoint puede intentar primero activar cualquiera de las características que depende de la característica. Para obtener más información, consulte [Cómo: agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Cómo: Agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  