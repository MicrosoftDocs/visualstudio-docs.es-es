---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a &#39;Declare&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a &#39;Declare&#39;
El atributo `DllImportAttribute` se aplicó a una función `Declare`. Este atributo solo se puede utilizar con un elemento `Function` o `Sub` vacíos.  
  
 **Id. de error:** BC31523  
  
### Para corregir este error  
  
1.  Quite el atributo `DllImportAttribute` de la instrucción `Declare`.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)