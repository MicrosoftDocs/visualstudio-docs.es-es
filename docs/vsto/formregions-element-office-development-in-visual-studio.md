---
title: "Elemento &lt;formRegions&gt; (desarrollo de Office en Visual Studio)"
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
  - "formRegions (elemento)"
  - "elemento <formRegions> "
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <formRegions>"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;formRegions&gt; (desarrollo de Office en Visual Studio)
  El elemento `formRegions` del espacio de nombres `vstov4`  contiene las áreas del formulario de Microsoft Office Outlook que están asociadas a un complemento VSTO.  
  
## Sintaxis  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## Elementos y atributos  
 El elemento `formRegions` del espacio de nombres `vstov4`  contiene todos los elementos `formRegion` para un complemento VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.  
  
 Sólo se puede definir un elemento `formRegions` en un manifiesto de aplicación.  
  
 El elemento `formRegions` no tiene atributos.  
  
 El elemento `formRegions` tiene el siguiente elemento:  
  
### formRegion  
 Es necesario para complementos VSTO de Outlook que incluyen áreas de formulario. El elemento `formRegion` se define en [Elemento &#60;formRegion&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## Ejemplo para complemento de VSTO  
  
### Descripción  
 El ejemplo de código siguiente muestra un elemento `formRegions` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  