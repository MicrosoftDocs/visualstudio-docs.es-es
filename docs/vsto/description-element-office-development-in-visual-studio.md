---
title: "Elemento &lt;description&gt; (desarrollo de Office en Visual Studio) | Microsoft Docs"
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
  - "description (elemento)"
  - "elemento <description>"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <description>"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Elemento &lt;description&gt; (desarrollo de Office en Visual Studio)
  El elemento `description` del espacio de nombres `vstov4`  almacena la descripción de la solución de Office que aparece en el cuadro de diálogo de complementos COM de aplicaciones de Microsoft Office.  
  
## Sintaxis  
  
```  
<description>  
</description>  
```  
  
## Elementos y atributos  
 Opcional. El elemento `description` está en el espacio de nombres `vstov4` . Contiene la descripción del complemento que se muestra en el cuadro de diálogo Complementos COM de las aplicaciones de Microsoft Office.  
  
 El elemento `description` no tiene atributos ni elementos secundarios.  
  
## Ejemplo para complemento de VSTO  
  
### Descripción  
 En el siguiente ejemplo de código se muestra el elemento `description` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  