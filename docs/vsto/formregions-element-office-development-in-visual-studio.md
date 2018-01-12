---
title: '&lt;formRegions&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eb7008f86dd552eac2b8a6ba9b227884270c8694
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `formRegions` del espacio de nombres `vstov4` contiene las áreas del formulario de Microsoft Office Outlook que están asociadas a un complemento VSTO.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `formRegions` del espacio de nombres `vstov4` contiene todos los elementos `formRegion` para un complemento VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.  
  
 Sólo se puede definir un elemento `formRegions` en un manifiesto de aplicación.  
  
 El elemento `formRegions` no tiene atributos.  
  
 El elemento `formRegions` tiene el siguiente elemento:  
  
### <a name="formregion"></a>formRegion  
 Es necesario para complementos VSTO de Outlook que incluyen áreas de formulario. El `formRegion` elemento se define en [&#60; formRegion &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra un elemento `formRegions` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  