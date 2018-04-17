---
title: '&lt;descripción&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13755a20b091696bf741c1f25360941e01b65945
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;descripción&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `description` del espacio de nombres `vstov4` almacena la descripción de la solución de Office que aparece en el cuadro de diálogo de complementos COM de aplicaciones de Microsoft Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 Opcional. El elemento `description` está en el espacio de nombres `vstov4` . Contiene la descripción del complemento que se muestra en el cuadro de diálogo Complementos COM de las aplicaciones de Microsoft Office.  
  
 El elemento `description` no tiene atributos ni elementos secundarios.  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>description  
 En el siguiente ejemplo de código se muestra el elemento `description` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  