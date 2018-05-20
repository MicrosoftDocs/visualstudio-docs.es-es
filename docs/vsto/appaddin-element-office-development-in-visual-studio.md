---
title: '&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0defe437e0778ee9d3c134148a3ca7e4b4cd2ef9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio)
  El **appAddin** elemento de la `vstov4` espacio de nombres almacena información específica de la personalización de complementos VSTO.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml 
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
 El **appAddin** elemento es necesario y se encuentra en la `vstov4` espacio de nombres. Solo hay un **appAddin** elemento definido en un manifiesto de aplicación.  
  
 El **appAddin** elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Aplicación**|Requerido. Identifica la aplicación de Microsoft Office. El valor puede ser uno de los siguientes: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|**loadBehavior**|Opcional. De forma predeterminada, el **loadBehavior** se habilita al establecer este valor en. Para la depuración, el complemento de VSTO puede deshabilitarse si establece el valor en dos. Para obtener más información, vea la tabla denominada LoadBehavior Values en [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**keyName**|Requerido. Este valor es el nombre de clave del Registro que la aplicación utilizará para cargar el complemento de VSTO. Para obtener más información, consulte [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 El **appAddin** elemento tiene los siguientes elementos secundarios.  
  
### <a name="friendlyname"></a>friendlyName  
 Opcional. El **friendlyName** elemento se explica en [ &#60;friendlyName&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Descripción  
 Opcional. El **descripción** elemento se explica en [ &#60;descripción&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario. El **formRegions** elemento se explica en [ &#60;formRegions&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Ejemplo para complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra **appAddin** elementos en una solución de Outlook implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
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
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  