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
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952754"
---
# <a name="create-sharepoint-features"></a>Crear características de SharePoint
  Puede usar una característica de SharePoint para agrupar los elementos de proyecto de SharePoint relacionados para facilitar la implementación. Puede crear características, establecer ámbitos y marcar otras características como dependencias mediante el diseñador de características de SharePoint. El diseñador también genera un manifiesto, que es un archivo XML que describe cada característica.

## <a name="add-features-to-the-sharepoint-solution"></a>Agregar características a la solución de SharePoint
 Puede Agregar una característica a la solución de SharePoint mediante Explorador de soluciones o el explorador de empaquetado. Puede usar uno de los métodos siguientes para agregar una característica.

- En **Explorador de soluciones**, abra el menú contextual de **características**y, a continuación, elija **Agregar característica**.

- En el **Explorador de empaquetado**, abra el menú contextual del paquete y, a continuación, elija **Agregar característica**.

## <a name="using-the-feature-designer"></a>Usar el diseñador de características
 Una solución de SharePoint puede contener una o varias características de SharePoint, que se agrupan bajo el nodo de características en Explorador de soluciones. Cada característica tiene su propio **Diseñador de características** que puede usar para personalizar las propiedades de la característica. Para obtener más información, consulte [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Para distinguir entre otras características, puede configurar las propiedades de la característica, como el título, la descripción, la versión y el ámbito.

### <a name="feature-designer-options"></a>Opciones del diseñador de características
 Después de crear una característica, puede usar el diseñador de características para personalizarla.

 En la tabla siguiente se describen las propiedades de las características que se muestran en el diseñador de características.

|Propiedad|Descripción|
|--------------|-----------------|
|Título|Opcional. El título predeterminado de la característica se establece en *solutionname* *FeatureName*.|
|Descripción|Opcional. La descripción de la característica de SharePoint.|
|Ámbito|Necesario. Si una característica se crea con **Explorador de soluciones**, el ámbito se establece en Web de forma predeterminada.<br /><br /> -Farm: activa una característica para una granja de servidores completa.<br /><br /> -Site: activa una característica para todos los sitios web de una colección de sitios.<br /><br /> -Web: activa una característica para un sitio web específico.<br /><br /> -WebApplication: activa una característica para todos los sitios web de una aplicación Web.|
|Elementos de la solución|Todos los elementos de SharePoint que se pueden agregar a la característica.|
|Elementos de la característica|Los elementos de proyecto de SharePoint que se han agregado a la característica.|

## <a name="add-and-remove-sharepoint-project-items"></a>Agregar y quitar elementos de proyecto de SharePoint
 Puede seleccionar los elementos de proyecto de SharePoint a los que desea agregar una característica de SharePoint para la implementación. Use el **Diseñador de características** para agregar y quitar elementos de las características y ver el manifiesto de la característica. Para obtener más información, vea [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Agregar dependencias de características
 Puede configurar el manifiesto de la característica para que el servidor de SharePoint Active ciertas características antes de que se active la característica. Por ejemplo, si la característica de SharePoint depende de otras características para la funcionalidad o los datos, el servidor de SharePoint puede intentar primero activar cualquiera de las características de las que depende la característica. Para obtener más información, consulte [Cómo: agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Consulte también
- [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Cómo: agregar y quitar dependencias de características](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
