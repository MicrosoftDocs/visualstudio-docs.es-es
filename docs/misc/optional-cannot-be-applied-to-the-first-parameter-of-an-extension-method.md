---
title: "&#39;Opcional&#39; no se puede aplicar al primer par&#225;metro de un m&#233;todo de extensi&#243;n. | Microsoft Docs"
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
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Opcional&#39; no se puede aplicar al primer par&#225;metro de un m&#233;todo de extensi&#243;n.
'Opcional' no se puede aplicar al primer parámetro de un método de extensión. El primer parámetro especifica el tipo que se debe extender.  
  
 El primer parámetro de un método de extensión especifica el tipo de datos que extiende el método. Cuando se ejecuta el método, el primer parámetro se enlaza a la instancia del tipo de datos que invoca el método. Por lo tanto, el primer parámetro es necesario y no puede ser opcional.  
  
 La restricción se aplica solo al primer parámetro. Otros parámetros pueden ser opcionales o no, siguiendo las mismas reglas que en cualquier otro método. Para obtener más información, consulta [Lista de parámetros](/dotnet/visual-basic/language-reference/statements/parameter-list).  
  
 **Identificador de error:** BC36553  
  
### Para corregir este error  
  
-   Si quiere que el primer parámetro actual especifique el tipo de datos que se va a extender, quite la palabra clave `Optional`.  
  
-   Si el primer parámetro actual es un parámetro estándar para el método y no quiere que represente el tipo de datos que se va a extender, agregue un nuevo primer parámetro.  
  
## Ejemplo  
 El primer parámetro del ejemplo siguiente es la única indicación de que el método `Print` extiende el tipo de datos `String`. Por lo tanto, no puede ser opcional.  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Cuando el método de extensión se llama como sigue, el parámetro `str` del método se enlaza a `greeting`, la instancia de `String` que llama a `Print`. El compilador usa `greeting` como argumento para el método de extensión `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Cómo: Definir parámetros opcionales para un procedimiento \(Visual Basic\)](http://msdn.microsoft.com/es-es/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Parámetros opcionales](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)