---
title: "Elemento &lt;customization&gt; (desarrollo de Office en Visual Studio)"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <customization>"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;customization&gt; (desarrollo de Office en Visual Studio)
  El elemento `customization` del espacio de nombres `vstov4` describe una solución de Office específica. Los elementos secundarios son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
## Sintaxis de las personalizaciones de nivel de documento  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## Sintaxis de los complementos de VSTO  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## Elementos y atributos  
 El elemento `customization` contiene información específica de la personalización. Este elemento debe estar en el espacio de nombres siguiente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Hay un elemento `customization` para cada solución de Office. Por ejemplo, si implementa tres soluciones de Office en una implementación de varios proyectos, hay tres elementos `customization` en el manifiesto de aplicación.  
  
 Los elementos secundarios del ensamblado también deben estar en este espacio de nombres.  
  
 El elemento `customization` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`id`|Obligatorio en implementaciones de varios proyectos. El elemento `id` identifica de forma única una solución de Office.|  
  
### Personalizaciones de nivel de documento  
 El elemento `customization` tiene el siguiente elemento secundario:  
  
#### documento  
 El elemento `document` del espacio de nombres `vstov4` se define en [Elemento &#60;document&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### Complementos de VSTO  
 El elemento `customization` tiene el siguiente elemento secundario:  
  
#### appAddin  
 El elemento `appAddin` del espacio de nombres `vstov4` se define en [Elemento &#60;appAddin&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## Ejemplo de personalización de nivel de documento  
  
### Descripción  
 En el ejemplo de código siguiente se muestra el elemento `customization` para una personalización de nivel de documento. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## Ejemplo de un complemento de VSTO  
  
### Descripción  
 En el ejemplo de código siguiente se muestra el elemento `customization` para un complemento de VSTO. Este es un complemento de VSTO para Outlook que incluye áreas de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  