---
title: '&lt;formRegion&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0c34dc6e3cc7fd9339e9f2a183bcc11d54008e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `formRegion` del espacio de nombres `vstov4` identifica un área de formulario de Microsoft Office Outlook que está asociada a un complemento de VSTO.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `formRegion` del espacio de nombres `vstov4` identifica un área de formulario asociada a un complemento de VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.  
  
 Puede haber varios elementos `formRegion` definidos dentro de un elemento `formRegions` para un único complemento de VSTO.  
  
 El elemento `formRegion` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Obligatorio. Identifica el nombre del área de formulario.|  
  
 El elemento `formRegion` tiene los siguientes elementos secundarios.  
  
### <a name="messageclass"></a>messageClass  
 El elemento `messageClass` identifica el formulario de Outlook que está asociado al área de formulario.  
  
 El elemento `messageClass` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Obligatorio. Identifica el formulario asociado a este área de formulario.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `formRegion` en un manifiesto de aplicación para un complemento de VSTO de Outlook implementado mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Hay tres clases de mensajes asociadas a esta área de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  