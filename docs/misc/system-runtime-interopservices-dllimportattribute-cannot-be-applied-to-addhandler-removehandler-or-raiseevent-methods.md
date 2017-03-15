---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a los m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39;. | Microsoft Docs"
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
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a los m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39;.
El atributo `DllImportAttribute` se aplicó a una declaración de método `AddHandler`, `RemoveHandler` o `RaiseEvent`. Este atributo solo se puede usar con un elemento `Function` o `Sub` vacíos.  
  
 **Identificador de error:** BC31531  
  
### Para corregir este error  
  
-   Quite el atributo `DllImportAttribute` de la declaración del método.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)