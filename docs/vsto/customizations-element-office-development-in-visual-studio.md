---
title: "&lt;customizations&gt; (elemento, Desarrollo de Office en Visual Studio) | Microsoft Docs"
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
  - "<customizations> (elemento)"
  - "customizations (elemento)"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <customizations>"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;customizations&gt; (elemento, Desarrollo de Office en Visual Studio)
  El elemento `customizations` del espacio de nombres `vstov4` contiene toda la información sobre la instalación y carga de cada solución de Office.  
  
## Sintaxis de las personalizaciones de nivel de documento  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## Sintaxis de los complementos de VSTO  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## Elementos y atributos  
 El elemento `customizations` contiene información específica sobre cada solución de Office. Este elemento debe estar en el espacio de nombres siguiente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Los elementos secundarios del ensamblado también deben estar en este espacio de nombres.  
  
 El elemento `customizations` no tiene atributos.  
  
 El elemento `customizations` tiene el siguiente elemento secundario:  
  
### personalización  
 Obligatorio. El elemento `customization` del espacio de nombres `vstov4` se define en [Elemento &#60;customization&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Ejemplo de personalización de nivel de documento  
  
### Descripción  
 En el ejemplo de código siguiente se muestra el elemento `customizations` para una personalización de nivel de documento.  
  
> [!NOTE]  
>  Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## Ejemplo de un complemento de VSTO  
  
### Descripción  
 En el ejemplo de código siguiente se muestra el elemento `customizations` para un complemento de VSTO. Este es un complemento de VSTO para Outlook que incluye áreas de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  