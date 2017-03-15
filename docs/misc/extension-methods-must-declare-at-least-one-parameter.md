---
title: "Los m&#233;todos de extensi&#243;n deben declarar al menos un par&#225;metro | Microsoft Docs"
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
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos de extensi&#243;n deben declarar al menos un par&#225;metro
Los métodos de extensión deben declarar al menos un parámetro. El primer parámetro especifica el tipo que se debe extender.  
  
 Un método de extensión sin parámetros no es válido porque el primer parámetro especifica qué tipo de datos extiende el método. El primer parámetro se enlaza a la instancia del tipo de datos que invoca el método.  
  
 **Identificador de error:** BC36552  
  
### Para corregir este error  
  
-   Agregue un parámetro del tipo que extiende el método.  
  
## Ejemplo  
 El primer parámetro del ejemplo siguiente indica que el método `Print` extiende el tipo de datos `String`.  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Cuando el método de extensión se llama como se indica a continuación, el parámetro `str` del método se enlaza a `greeting`, la instancia de `String` que llama a `Print`. El compilador usará `greeting` como argumento para el método de extensión `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Argumentos y parámetros de procedimiento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)