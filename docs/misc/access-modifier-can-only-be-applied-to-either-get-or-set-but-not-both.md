---
title: "El modificador de acceso solo se puede aplicar a &#39;Get&#39; o &#39;Set&#39;, no a ambos | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El modificador de acceso solo se puede aplicar a &#39;Get&#39; o &#39;Set&#39;, no a ambos
Una declaración de propiedad especifica niveles de acceso en la [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement), la [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) y la [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Siempre puede especificar un nivel de acceso para la propiedad. Además, puede especificar un nivel de acceso diferente para al menos uno de los procedimientos de la propiedad \(`Get` o `Set`\), siempre que sea más restrictivo que el nivel de acceso de la propiedad. No puede especificar niveles de acceso para ambos procedimientos de la propiedad.  
  
 **Identificador de error:** BC31101  
  
### Para corregir este error  
  
-   Quite el modificador de acceso de la instrucción `Get` o la instrucción `Set`.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)