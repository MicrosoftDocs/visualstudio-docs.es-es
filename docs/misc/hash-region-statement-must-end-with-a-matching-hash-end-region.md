---
title: "La instrucci&#243;n &#39;#Region&#39; debe terminar con una instrucci&#243;n &#39;#End Region&#39; correspondiente | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;#Region&#39; debe terminar con una instrucci&#243;n &#39;#End Region&#39; correspondiente
La directiva `#Region` permite especificar un bloque de código que puede expandir o contraer cuando use la característica de esquematización del Editor de código de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El inicio y fin de las instrucciones `#Region` deben estar en el mismo bloque de código.  
  
 **Id.de error:** BC30681  
  
### Para corregir este error  
  
1.  Inserte `#End Region` en el lugar adecuado del código después de la instrucción `#Region`.  
  
## Vea también  
 [\#Region \(Directiva\)](/dotnet/visual-basic/language-reference/directives/region-directive)