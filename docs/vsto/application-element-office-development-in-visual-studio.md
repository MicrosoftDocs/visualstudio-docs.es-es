---
title: "Elemento &lt;application&gt; (desarrollo de Office en Visual Studio)"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <application>"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Elemento &lt;application&gt; (desarrollo de Office en Visual Studio)
  El elemento `application` del espacio de nombres `vstav3` contiene la descripción de las soluciones de Office. Los elementos secundarios son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
## Sintaxis de las personalizaciones de nivel de documento  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## Sintaxis de los complementos de nivel de aplicación  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## Elementos y atributos  
 El elemento `application` del espacio de nombres `vstav3` es el nodo que encapsula toda la información específica de la personalización que se encuentra en el espacio de nombres `vstov4`.  
  
 El elemento `application` no tiene atributos.  
  
 El elemento `application` tiene el elemento siguiente:  
  
### personalización  
 El rol del elemento `customization` en el espacio de nombres `vstov3` se define en [Elemento &#60;customization&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Ejemplo de personalización de nivel de documento  
  
### Descripción  
 En el siguiente ejemplo de código se muestra un elemento `application` en una solución de Office de nivel de documento implementada con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Ejemplo de complemento de VSTO  
  
### Descripción  
 En el siguiente ejemplo de código se muestra un elemento `application` en una solución de Office de nivel de aplicación implementada con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  