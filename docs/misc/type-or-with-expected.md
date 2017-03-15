---
title: "Se esperaba un tipo o &#39;With&#39;. | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba un tipo o &#39;With&#39;.
Cuando se declara una instancia de una clase, la palabra clave `New` debe ir seguida por un nombre de tipo o por `With`. Por ejemplo, las instrucciones siguientes declaran `client` como una instancia de la clase `Customer`. El nombre del tipo `Customer` sigue a `New`.  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 A partir de [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)], puede declarar un objeto como una instancia de un tipo anónimo, en cuyo caso no se especifica un tipo de datos. En declaraciones de tipos anónimos, la palabra clave `With` sigue a `New`.  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **Identificador de error:** BC30988  
  
### Para corregir este error  
  
-   Cambie la declaración para que `With` o un nombre de tipo siga a `New`.  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Instrucciones NotInBuild:Declaration en Visual Basic](http://msdn.microsoft.com/es-es/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)