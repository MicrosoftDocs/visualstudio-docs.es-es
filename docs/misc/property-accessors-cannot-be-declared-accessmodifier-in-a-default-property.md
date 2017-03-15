---
title: "Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;modificadorDeAcceso&gt;&#39; en una propiedad &#39;Default&#39; | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;modificadorDeAcceso&gt;&#39; en una propiedad &#39;Default&#39;
Una [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) o [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement) de una propiedad predeterminada incluye la palabra clave `Private`.  
  
 Una propiedad predeterminada no puede ser `Private` y tampoco pueden serlo sus procedimientos de propiedad individuales \(`Get` o `Set`\).  
  
 **Identificador de error:** BC31107  
  
### Para corregir este error  
  
-   Quite la palabra clave `Private` de la instrucción `Get` o `Set` o quite `Default` de [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement).  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Cómo: Declarar y llamar a una propiedad predeterminada en Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)