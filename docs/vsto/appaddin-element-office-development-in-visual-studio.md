---
title: '&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 27f286f9bde8db68a7190796f1d154a402fb208d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `appAddin` del espacio de nombres `vstov4` almacena información específica de la personalización de los complementos de VSTO.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `appAddin` es obligatorio y se encuentra en el espacio de nombres `vstov4` . Solo hay un elemento `appAddin` definido en un manifiesto de aplicación.  
  
 El elemento `appAddin` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`application`|Requerido. Identifica la aplicación de Microsoft Office. El valor puede ser uno de los siguientes: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|`loadBehavior`|Opcional. De forma predeterminada, `loadBehavior` se habilita al establecer este valor en . Para la depuración, el complemento de VSTO puede deshabilitarse si establece el valor en dos. Para más información, consulte la tabla denominada LoadBehavior Values en [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Requerido. Este valor es el nombre de clave del Registro que la aplicación utilizará para cargar el complemento de VSTO. Para obtener más información, consulta [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 El elemento `appAddin` tiene los siguiente elementos secundarios:  
  
### <a name="friendlyname"></a>friendlyName  
 Opcional. El `friendlyName` elemento se explica en [&#60; friendlyName &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Descripción  
 Opcional. El `description` elemento se explica en [&#60; descripción &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario. El `formRegions` elemento se explica en [&#60; formRegions &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestran elementos `appAddin` en una solución de Outlook implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:appAddIn   
  application="Outlook"   
  loadBehavior="3"   
  keyName="ContosoOutlookAddIn">  
  <vstov4:friendlyName>  
    ContosoOutlookAddIn  
  </vstov4:friendlyName>  
  <vstov4:description>  
    ContosoOutlookAddIn - Outlook VSTO Add-in   
    created with Visual Studio Tools for Office  
  </vstov4:description>  
  <vstov4:formRegions>  
    <vstov4:formRegion  
        name="OutlookAddIn1.FormRegion1">  
      <vstov4:messageClass name="IPM.Note" />  
      <vstov4:messageClass name="IPM.Contact" />  
      <vstov4:messageClass name="IPM.Appointment" />  
    </vstov4:formRegion>  
  </vstov4:formRegions>  
</vstov4:appAddIn>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  