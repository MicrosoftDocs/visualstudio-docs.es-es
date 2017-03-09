---
title: "Los m&#233;todos de extensi&#243;n solo se pueden definir en m&#243;dulos | Microsoft Docs"
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
  - "vbc36551"
  - "bc36551"
helpviewer_keywords: 
  - "BC36551"
ms.assetid: c832d523-5bf6-4baf-b91c-bd26d94453ed
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos de extensi&#243;n solo se pueden definir en m&#243;dulos
Este error se produce si un método de extensión se ha definido fuera de un módulo. En Visual Basic, todos los métodos de extensión se deben definir dentro de los módulos estándares.  
  
 **Id. de error:** BC36551  
  
### Para corregir este error  
  
-   Coloque el método de extensión en un módulo.  
  
## Ejemplo  
 En el ejemplo siguiente se amplía la clase `String` agregando un método `Print`.  
  
```  
Imports StringUtility Imports System.Runtime.CompilerServices Namespace StringUtility <Extension()> _ Module StringExtensions <Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub End Module End Namespace  
```  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Module \<palabra clave\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement)