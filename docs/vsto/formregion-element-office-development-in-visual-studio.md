---
title: "Elemento &lt;formRegion&gt; (desarrollo de Office en Visual Studio)"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <formRegion>"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Elemento &lt;formRegion&gt; (desarrollo de Office en Visual Studio)
  El elemento `formRegion` del espacio de nombres `vstov4`  identifica un área de formulario de Microsoft Office Outlook que está asociada a un complemento de VSTO.  
  
## Sintaxis  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Elementos y atributos  
 El elemento `formRegion` del espacio de nombres `vstov4`  identifica un área de formulario asociada a un complemento de VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.  
  
 Puede haber varios elementos `formRegion` definidos dentro de un elemento `formRegions` para un único complemento de VSTO.  
  
 El elemento `formRegion` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio. Identifica el nombre del área de formulario.|  
  
 El elemento `formRegion` tiene los siguientes elementos secundarios.  
  
### messageClass  
 El elemento `messageClass`  identifica el formulario de Outlook que está asociado al área de formulario.  
  
 El elemento `messageClass` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio. Identifica el formulario asociado a este área de formulario.|  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `formRegion` en un manifiesto de aplicación para un complemento de VSTO de Outlook implementado mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Hay tres clases de mensajes asociadas a esta área de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  