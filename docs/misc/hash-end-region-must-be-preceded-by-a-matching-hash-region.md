---
title: "&#39;#End Region&#39; debe ir precedida de la instrucci&#243;n &#39;#Region&#39; correspondiente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; debe ir precedida de la instrucci&#243;n &#39;#Region&#39; correspondiente
`#Region` permite especificar que un bloque de código se expanda o contraiga cuando se use la característica de esquematización del Editor de código de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El inicio y fin de las instrucciones `#Region` deben estar en el mismo bloque de código.  
  
 **Identificador de error:** BC30680  
  
### Para corregir este error  
  
-   Inserte `#Region` en el lugar adecuado antes de la instrucción `#End` `Region` correspondiente.  
  
## Vea también  
 [\#Region \(Directiva\)](/dotnet/visual-basic/language-reference/directives/region-directive)