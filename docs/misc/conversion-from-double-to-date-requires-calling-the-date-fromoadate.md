---
title: "La conversi&#243;n de &#39;Double&#39; en &#39;Date&#39; requiere llamar a &#39;Date.FromOADate&#39;. | Microsoft Docs"
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
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La conversi&#243;n de &#39;Double&#39; en &#39;Date&#39; requiere llamar a &#39;Date.FromOADate&#39;.
Intentó convertir un valor `Date` en un valor `Double`, lo que no se puede realizar sin usar el método <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>.  
  
 **Identificador de error:** BC30533  
  
### Para corregir este error  
  
-   Use el método <xref:System.DateTime.FromOADate%2A> para convertir el valor.  
  
## Vea también  
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)