---
title: '&lt;documento&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38b03c2a4980891d9a6841b24365db32ee555de4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
 `document`no tiene elementos secundarios.  
  
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
  
  