---
title: "&#39;&lt;nombreM&#233;todo&gt;&#39; no es accesible en este contexto porque el tipo de valor devuelto no es accesible. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36665"
  - "vbc36666"
  - "bc36666"
  - "vbc36665"
helpviewer_keywords: 
  - "BC36666"
  - "BC36665"
ms.assetid: 8f29eb7e-351f-486c-9d1f-3556cc11b7c5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreM&#233;todo&gt;&#39; no es accesible en este contexto porque el tipo de valor devuelto no es accesible.
Se llamó a una función que tiene un tipo de valor devuelto al que no puede acceder desde la instrucción de llamada. Por ejemplo, en el código siguiente, la llamada desde `Main` a `PublicMethod` produce un error porque el tipo de valor devuelto, `PrivateType`, se declara con el modificador de acceso `Private` en la clase `TestClass`. Por lo tanto, el contexto en el que se puede acceder a `PrivateType` está limitado a `TestClass`.  
  
```vb#  
Class TestClass  
  
    Dim pT As New PrivateType  
  
    Private Class PrivateType  
    End Class  
  
    '' A corresponding error is returned in this line: 'PublicMethod   
    '' cannot expose 'PrivateType' in namespace 'ConsoleApplication1'   
    '' through class 'TestClass'.  
    'Public Function PublicMethod() As PrivateType  
    '    Return Nothing  
    'End Function  
  
End Class  
  
Module Module1  
  
    Sub Main()  
  
        Dim tc As TestClass  
        '' This error occurs here, because the data type returned by   
        '' PublicMethod()is declared Private in class TestClass and   
        '' cannot be accessed from here.  
        'Console.WriteLine(tc.PublicMethod())  
  
    End Sub  
  
End Module  
```  
  
 **Identificador de error:** BC36665 y BC36666  
  
### Para corregir este error  
  
-   Si la definición de tipo es accesible, cambie el modificador de acceso de `Private` a `Public`.  
  
-   Cambie el tipo de valor devuelto de la función si tiene acceso a él.  
  
-   Escriba un método o el método de extensión que devuelva un tipo accesible.  
  
## Vea también  
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)