---
title: "Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;modificadorDeAcceso&gt;&#39; en una propiedad &#39;NotOverridable&#39; | Microsoft Docs"
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
  - "vbc31106"
  - "bc31106"
helpviewer_keywords: 
  - "BC31106"
ms.assetid: 84bcb157-9c33-4e4f-89a9-c5e6cb73028b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;modificadorDeAcceso&gt;&#39; en una propiedad &#39;NotOverridable&#39;
Una [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) o [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement) de una propiedad `NotOverridable` incluye la palabra clave `Private`.  
  
 La línea de razonamiento siguiente explica por qué `NotOverridable` y `Private` no se pueden combinar en una [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement):  
  
1.  Una propiedad o un procedimiento que no reemplaza una propiedad de clase base o un procedimiento tiene un valor predeterminado de [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable).  
  
2.  Sin embargo, una propiedad o un procedimiento de una clase derivada que reemplaza una propiedad de clase base o un procedimiento tiene un valor predeterminado de [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable). Para finalizar la jerarquía de reemplazo, puede declararla `NotOverridable`. Este es el único contexto en que se puede usar `NotOverridable`. Es decir, solo puede usar `NotOverridable` en combinación con [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides).  
  
3.  Si se declara una propiedad de clase base o un procedimiento [Private](/dotnet/visual-basic/language-reference/modifiers/private), una clase derivada no puede reemplazar esa propiedad o ese procedimiento porque no puede acceder a estos. Por este motivo, no puede usar `Private` en combinación con `Overridable`.  
  
4.  Para reemplazar una propiedad o un procedimiento, la propiedad o el procedimiento de reemplazo no solo debe tener la firma idéntica, sino también el mismo nivel de acceso. Esto significa que no una propiedad o procedimiento de reemplazo no pueden especificar `Private`, porque una propiedad o un procedimiento reemplazables no pueden especificar `Private`.  
  
5.  Dado que puede especificar `NotOverridable` solo en una propiedad o un procedimiento de reemplazo, no se puede combinar con `Private`.  
  
 Siguiendo el mismo razonamiento, los procedimientos de propiedades individuales \(`Get` y `Set`\) de una propiedad de reemplazo no pueden ser `Private`.  
  
 **Identificador de error:** BC31106  
  
### Para corregir este error  
  
-   Quite la palabra clave `Private` de la instrucción `Get` o `Set`, o bien quite las palabras clave `Overrides` y `NotOverridable` de la instrucción `Property`.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Diferencias entre sombrear y reemplazar](/dotnet/visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)