---
title: "Las propiedades &#39;WriteOnly&#39; no pueden tener un modificador de acceso en &#39;Set&#39; | Microsoft Docs"
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
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las propiedades &#39;WriteOnly&#39; no pueden tener un modificador de acceso en &#39;Set&#39;
Una declaración de la propiedad `WriteOnly` especifica niveles de acceso tanto en el elemento [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement) como en el elemento [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Siempre puede especificar un nivel de acceso para la propiedad. Además, puede especificar un nivel de acceso diferente para como máximo uno de los procedimientos de la propiedad \(`Get` o `Set`\), siempre que sea más restrictivo que el nivel de acceso de la propiedad. No puede especificar niveles de acceso para ambos procedimientos de la propiedad.  
  
 **Id. de error:** BC31104  
  
### Para corregir este error  
  
-   Quite el modificador de acceso de la instrucción `Set`. Representa toda la propiedad `WriteOnly` y no puede tener dos niveles de acceso para la propiedad.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)