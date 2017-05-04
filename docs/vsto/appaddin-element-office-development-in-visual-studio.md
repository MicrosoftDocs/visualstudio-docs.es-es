---
title: "Elemento &lt;appAddin&gt; (desarrollo de Office en Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <appAddin>"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Elemento &lt;appAddin&gt; (desarrollo de Office en Visual Studio)
  El elemento `appAddin` del espacio de nombres `vstov4`  almacena información específica de la personalización de los complementos de VSTO.  
  
## Sintaxis  
  
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
  
## Elementos y atributos  
 El elemento `appAddin` es obligatorio y se encuentra en el espacio de nombres `vstov4` . Solo hay un elemento `appAddin` definido en un manifiesto de aplicación.  
  
 El elemento `appAddin` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`application`|Obligatorio. Identifica la aplicación de Microsoft Office. El valor puede ser uno de los siguientes: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|`loadBehavior`|Opcional. De forma predeterminada, `loadBehavior` se habilita al establecer este valor en . Para la depuración, el complemento de VSTO puede deshabilitarse si establece el valor en dos. Para más información, consulte la tabla denominada LoadBehavior Values en [Entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Obligatorio. Este valor es el nombre de clave del Registro que la aplicación utilizará para cargar el complemento de VSTO. Para obtener más información, consulta [Entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 El elemento `appAddin` tiene los siguiente elementos secundarios:  
  
### friendlyName  
 Opcional. El elemento `friendlyName` se explica en [&#60;friendlyName&#62; &#40;elemento&#41; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### Descripción  
 Opcional. El elemento `description` se explica en [Elemento &#60;description&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### formRegions  
 Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario. El elemento `formRegions` se explica en [Elemento &#60;formRegions&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## Ejemplo para complemento de VSTO  
  
### Descripción  
 En el ejemplo de código siguiente se muestran elementos `appAddin` en una solución de Outlook implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  