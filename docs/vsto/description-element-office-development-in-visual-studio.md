---
title: "&lt;descripción&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft"
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2fdb8fb394ce2ccb7bb549df55ef1649b68d5cb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
  