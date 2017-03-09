---
title: "El m&#233;todo de extensi&#243;n &#39;&lt;methodName&gt;&#39; definido en &#39;&lt;typeName&gt;&#39; no tiene la misma firma que el delegado &#39;&lt;delegateName&gt;&#39;. | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo de extensi&#243;n &#39;&lt;methodName&gt;&#39; definido en &#39;&lt;typeName&gt;&#39; no tiene la misma firma que el delegado &#39;&lt;delegateName&gt;&#39;.
Hay un error de coincidencia entre las firmas del método de extensión y el delegado que está intentando usar. La instrucción `Delegate` define los tipos de parámetro y los tipos de valor devueltos de una clase de delegado. Cualquier procedimiento con parámetros coincidentes, tipos y tipos devueltos puede usarse para crear una instancia de este tipo de delegado. Este error se produce en el siguiente ejemplo, porque la firma del método de extensión `Example` no es compatible con la firma del delegado `Del`.  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **Identificador de error:** BC36580  
  
### Para corregir este error  
  
-   Compruebe que el delegado y el método de extensión tienen el mismo número de parámetros.  
  
-   Compruebe que el orden de los parámetros es el mismo en el delegado y el método de extensión.  
  
-   Comparar el tipo de datos de cada parámetro de delegado con el tipo de datos del parámetro correspondiente del método de extensión para asegurarse de que son compatibles.  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)