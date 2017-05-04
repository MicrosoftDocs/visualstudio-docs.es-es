---
title: "&lt;friendlyName&gt; (elemento) (desarrollo de Office en Visual Studio) | Microsoft Docs"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <friendlyName>"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;friendlyName&gt; (elemento) (desarrollo de Office en Visual Studio)
  El elemento`friendlyName` del espacio de nombres `vstov4` almacena el nombre que aparece en la lista de programas instalados.  
  
## Sintaxis  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## Elementos y atributos  
 El elemento `friendlyName` está en el espacio de nombres `vstov4` . El valor se muestra en la lista de programas instalados en el equipo y en el cuadro de diálogo de complementos de VSTO COM de las aplicaciones de Microsoft Office.  
  
 El elemento `friendlyName` no tiene atributos ni elementos secundarios.  
  
## Ejemplo de complemento de VSTO  
  
### Descripción  
 En el siguiente ejemplo de código se muestra el elemento `friendlyName` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  