---
title: "El modificador de acceso &#39;&lt;modificadorDeAcceso&gt;&#39; no es v&#225;lido | Microsoft Docs"
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
  - "bc31100"
  - "vbc31100"
helpviewer_keywords: 
  - "BC31100"
ms.assetid: 1cd71acc-0b54-4f64-8d61-75b272d293cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El modificador de acceso &#39;&lt;modificadorDeAcceso&gt;&#39; no es v&#225;lido
Una [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) o [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement) especifica un nivel de acceso menos restrictivo que el especificado para la propiedad contenedora.  
  
 Siempre puede especificar un nivel de acceso para la propiedad. Además, puede especificar un nivel de acceso diferente para al menos uno de los procedimientos de la propiedad \(`Get` o `Set`\), siempre que sea más restrictivo que el nivel de acceso de la propiedad. Por ejemplo, si la propiedad es `Friend`, puede especificar `Private` para un procedimiento de propiedad, pero no `Public`. No puede especificar niveles de acceso para ambos procedimientos de la propiedad.  
  
 **Identificador de error:** BC31100  
  
### Para corregir este error  
  
-   Haga que el nivel de acceso para el procedimiento de propiedad sea más restrictivo que para la propiedad o quite el modificador de acceso completamente.  
  
-   Declare el nivel de acceso menos restrictivo en la [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement) y declare el nivel de acceso más restrictivo en uno de los procedimientos de propiedad.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)