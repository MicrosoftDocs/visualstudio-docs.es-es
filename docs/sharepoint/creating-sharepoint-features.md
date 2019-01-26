---
title: Crear características de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58db8ea5affd295ec21ed9e398053c57345dee79
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862136"
---
# <a name="create-sharepoint-features"></a>Crear características de SharePoint
  Puede usar una característica de SharePoint para agrupar elementos relacionados del proyecto de SharePoint para una fácil implementación. Puede crear características, establecer ámbitos y marcar otras características como dependencias mediante el Diseñador de características de SharePoint. El diseñador también genera un manifiesto, que es un archivo XML que describe cada característica.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>Agregar características a la solución de SharePoint
 Puede agregar una característica a la solución de SharePoint mediante el Explorador de soluciones o el Explorador de empaquetado. Puede usar uno de los métodos siguientes para agregar una característica.  
  
-   En **el Explorador de soluciones**, abra el menú contextual para **características**y, a continuación, elija **Agregar característica**.  
  
-   En **Explorador de empaquetado**, abra el menú contextual para el paquete y, a continuación, elija **Agregar característica**.  
  
## <a name="using-the-feature-designer"></a>Utilizando el Diseñador de características
 Una solución de SharePoint puede contener una o varias características de SharePoint, que se agrupan bajo el nodo de función en el Explorador de soluciones. Cada característica tiene su propio **característica Diseñador** que puede usar para personalizar las propiedades de característica. Para obtener más información, vea [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Para distinguir las características entre sí, puede configurar las propiedades de características como el título, la descripción, la versión y el ámbito.  
  
### <a name="feature-designer-options"></a>Opciones del Diseñador de características
 Después de crear una característica, puede usar el Diseñador de características para personalizarlo.  
  
 En la tabla siguiente se describe las propiedades de características que se muestran en el Diseñador de características.  
  
|Property|Descripción|  
|--------------|-----------------|  
|Título|Opcional. El título predeterminado de la característica está establecido en *SolutionName* *FeatureName*.|  
|Descripción|Opcional. La descripción de la característica de SharePoint.|  
|Ámbito|Obligatorio. Si se crea con una característica **el Explorador de soluciones**, el ámbito se establece en Web de forma predeterminada.<br /><br /> -Granja de servidores: Activar una característica para una granja de servidores completa.<br /><br /> -Sitio: Activar una característica para todos los sitios web en una colección de sitios.<br /><br /> -Web: Activar una característica para un sitio web específico.<br /><br /> - WebApplication: Activar una característica para todos los sitios web en una aplicación web.|  
|Elementos de la solución|Todos los elementos de SharePoint que se pueden agregar a la característica.|  
|Elementos de la característica|Los elementos de proyecto de SharePoint que se han agregado a la característica.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Agregar y quitar elementos de proyecto de SharePoint
 Puede seleccionar qué elementos de proyecto de SharePoint que desea agregar una característica de SharePoint para la implementación. Use la **característica Diseñador** para agregar y quitar elementos de las características y ver el manifiesto de característica. Para obtener más información, vea [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Agregar dependencias de características
 Puede configurar el manifiesto de la característica para que el servidor de SharePoint activa determinadas características antes de que la característica está activada. Por ejemplo, si la característica de SharePoint depende de otras características para la funcionalidad o datos, el servidor de SharePoint puede intentar primero activar cualquiera de las características que depende de la característica. Para obtener más información, vea [Cómo: Agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Cómo: Agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
