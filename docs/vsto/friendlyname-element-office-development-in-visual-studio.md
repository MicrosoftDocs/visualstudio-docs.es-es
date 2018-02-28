---
title: '&lt;friendlyName&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 446a64c402ed9eb70b933b8c32f86426277564c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `friendlyName` del espacio de nombres `vstov4` almacena el nombre que aparece en la lista de programas instalados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `friendlyName` está en el espacio de nombres `vstov4` . El valor se muestra en la lista de programas instalados en el equipo y en el cuadro de diálogo de complementos de VSTO COM de las aplicaciones de Microsoft Office.  
  
 El elemento `friendlyName` no tiene atributos ni elementos secundarios.  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código se muestra el elemento `friendlyName` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  