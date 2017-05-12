---
title: "Elemento &lt;document&gt; (desarrollo de Office en Visual Studio)"
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
  - "documento (elemento)"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <document>"
  - "elemento <documento>"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Elemento &lt;document&gt; (desarrollo de Office en Visual Studio)
  El elemento `document` del espacio de nombres `vstov4`  almacena información específica de personalización para personalizaciones de nivel de documento.  
  
## Sintaxis  
  
```  
<document solutionId />  
```  
  
## Elementos y atributos  
 Sólo se requiere para las personalizaciones de nivel de documento.  El elemento `document` se encuentra en el espacio de nombres `vstov4` .  El elemento `document` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`solutionId`|Obligatorio.  GUID utilizado por el runtime de Visual Studio Tools para Office para identificar una solución de nivel de documento.  Este valor se almacena como la propiedad de documento personalizada \_AssemblyLocation.  Para obtener más información, vea [Información general sobre propiedades personalizadas del documento](../vsto/custom-document-properties-overview.md).|  
  
 `document` no tiene ningún elemento secundario.  
  
## Ejemplo de personalización de nivel de documento  
  
### Descripción  
 En el ejemplo de código siguiente se muestra el elemento `document` en una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  