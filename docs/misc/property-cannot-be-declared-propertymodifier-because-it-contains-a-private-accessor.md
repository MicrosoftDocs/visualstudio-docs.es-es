---
title: "La propiedad no se puede declarar como &#39;&lt;propertymodifier&gt;&#39; porque contiene un descriptor de acceso &#39;Private&#39;. | Microsoft Docs"
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
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad no se puede declarar como &#39;&lt;propertymodifier&gt;&#39; porque contiene un descriptor de acceso &#39;Private&#39;.
Una propiedad con un procedimiento de propiedad `Private` \(`Get` o `Set`\) está marcada como [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable).  
  
 Si se declara una propiedad de clase base o procedimiento [Private](/dotnet/visual-basic/language-reference/modifiers/private), una clase derivada no puede invalidar esa propiedad o procedimiento porque no puede tener acceso a estos. Por este motivo, no puede usar `Private` en combinación con `Overridable`. Esto se aplica no solo a la propiedad en sí, sino también a los procedimientos de propiedad individuales.  
  
 **Identificador de error:** BC31108  
  
### Para corregir este error  
  
-   Quite la palabra clave `Overridable` de [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement), o quite la palabra clave `Private` de [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) o [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)