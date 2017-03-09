---
title: "Las propiedades &#39;ReadOnly&#39; no pueden tener un modificador de acceso en &#39;Get&#39;. | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las propiedades &#39;ReadOnly&#39; no pueden tener un modificador de acceso en &#39;Get&#39;.
Una declaración de la propiedad `ReadOnly` especifica niveles de acceso tanto en la [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement) como en la [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement).  
  
 Siempre puede especificar un nivel de acceso para la propiedad. Además, puede especificar un nivel de acceso diferente para al menos uno de los procedimientos de la propiedad \(`Get` o `Set`\), siempre que sea más restrictivo que el nivel de acceso de la propiedad. No puede especificar niveles de acceso para ambos procedimientos de la propiedad.  
  
 **Identificador de error:** BC31105  
  
### Para corregir este error  
  
-   Quite el modificador de acceso de la instrucción `Get`. Representa toda la propiedad `ReadOnly` y no puede tener dos niveles de acceso para la propiedad.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)