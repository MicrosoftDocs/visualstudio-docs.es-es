---
title: '&lt;documento&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
ms.openlocfilehash: 0e33e638937a02589a08e3ba2bebf9d3e9aeb1a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (desarrollo de Office en Visual Studio)
  El `document` elemento de la `vstov4` espacio de nombres almacena información específica de la personalización para las personalizaciones de nivel de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 Solo se requiere para las personalizaciones de nivel de documento. El `document` elemento está en la `vstov4` espacio de nombres. El `document` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`solutionId`|Requerido. El GUID utilizado por Visual Studio Tools para Office runtime para identificar de forma única una solución de nivel de documento. Este valor se almacena como la propiedad de documento personalizada _AssemblyLocation. Para obtener más información, consulta [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).|  
  
 `document` no tiene elementos secundarios.  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra la `document` elemento en una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  