---
title: "No se puede realizar una conversi&#243;n de &#39;&lt;type1&gt;&#39; a &#39;&lt;type2&gt;&#39; en una expresi&#243;n constante que se usa como argumento de un atributo. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede realizar una conversi&#243;n de &#39;&lt;type1&gt;&#39; a &#39;&lt;type2&gt;&#39; en una expresi&#243;n constante que se usa como argumento de un atributo.
Una expresión usada para un argumento de atributo evalúa un tipo de datos distinto del parámetro de atributo correspondiente, y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no admite la conversión al tipo requerido para los argumentos de atributo.  
  
 Un atributo proporciona metadatos para el elemento al que se aplica, y el compilador debe poder construir todos los metadatos en tiempo de compilación. Por este motivo, todos los atributos deben utilizar valores que son constantes en tiempo de compilación y, por lo tanto, cada argumento de atributo debe evaluarse en un valor constante en tiempo de compilación.  
  
 Ciertas conversiones de tipos no pueden generar valores que son constantes en tiempo de compilación. Por ejemplo, convertir un `String` a un `Double` o un `Date` depende de la configuración regional en tiempo de ejecución. Otras conversiones, como una matriz de un tipo derivado a una matriz de `Object`, presentan una variedad de problemas que no permiten al compilador admitirlos en argumentos de atributo.  
  
 **Identificador de error:** BC30934  
  
### Para corregir este error  
  
-   Use una expresión que se evalúa como el mismo tipo de datos que el parámetro correspondiente, tal como se define por el atributo.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)