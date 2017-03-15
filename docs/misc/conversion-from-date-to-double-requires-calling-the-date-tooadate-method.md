---
title: "La conversi&#243;n de &#39;Date&#39; en &#39;Double&#39; requiere llamar al m&#233;todo &#39;Date.ToOADate&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La conversi&#243;n de &#39;Date&#39; en &#39;Double&#39; requiere llamar al m&#233;todo &#39;Date.ToOADate&#39;.
Intentó convertir un valor `Date` en un valor `Double`, lo que no se puede realizar sin usar el método <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.  
  
 **Identificador de error:** BC30532  
  
### Para corregir este error  
  
-   Use el método <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> para convertir el valor.  
  
## Vea también  
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)