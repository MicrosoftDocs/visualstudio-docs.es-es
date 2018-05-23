---
title: '&lt;documento&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (desarrollo de Office en Visual Studio)
  El `document` elemento de la `vstov4` espacio de nombres almacena información específica de la personalización para las personalizaciones de nivel de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 Solo se requiere para las personalizaciones de nivel de documento. El `document` elemento está en la `vstov4` espacio de nombres. El `document` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`solutionId`|Requerido. El GUID utilizado por Visual Studio Tools para Office runtime para identificar de forma única una solución de nivel de documento. Este valor se almacena como la propiedad de documento personalizada _AssemblyLocation. Para obtener más información, consulte [información general de propiedades de documento personalizado](../vsto/custom-document-properties-overview.md).|  
  
 `document` no tiene elementos secundarios.  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra la `document` elemento en una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  