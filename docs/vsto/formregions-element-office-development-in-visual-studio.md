---
title: '&lt;formRegions&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b978ef47db6b8803b7730aef14173c3eb19b16e8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674006"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; elemento (desarrollo de Office en Visual Studio)
  El `formRegions` elemento de la `vstov4` espacio de nombres contiene las áreas de formulario de Microsoft Office Outlook que están asociadas con un complemento de VSTO.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El elemento `formRegions` del espacio de nombres `vstov4` contiene todos los elementos `formRegion` para un complemento VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.  
  
 Sólo se puede definir un elemento `formRegions` en un manifiesto de aplicación.  
  
 El elemento `formRegions` no tiene atributos.  
  
 El elemento `formRegions` tiene el siguiente elemento:  
  
### <a name="formregion"></a>formRegion  
 Es necesario para complementos VSTO de Outlook que incluyen áreas de formulario. El `formRegion` elemento está definido en [ &#60;formRegion&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra un elemento `formRegions` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
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
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  