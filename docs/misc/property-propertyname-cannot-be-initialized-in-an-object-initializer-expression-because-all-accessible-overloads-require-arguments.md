---
title: "No se puede inicializar la propiedad &#39;&lt;propertyname&gt;&#39; en una expresi&#243;n de inicializador de objeto porque todas las sobrecargas accesibles requieren argumentos | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inicializar la propiedad &#39;&lt;propertyname&gt;&#39; en una expresi&#243;n de inicializador de objeto porque todas las sobrecargas accesibles requieren argumentos
Los miembros que se inicializan en una lista de inicializadores de objeto deben ser campos o propiedades. Además, las propiedades de una lista de inicializador no pueden tener parámetros. La propiedad que causa el error está sobrecargada y cada una de sus versiones requiere argumentos. Por lo tanto, la propiedad no se puede inicializar en una lista de inicializadores de objeto.  
  
 **Identificador de error:** BC30993  
  
### Para corregir este error  
  
-   Quite la propiedad que requiere argumentos de la lista de inicializadores.  
  
## Ejemplo  
 La siguiente clase contiene tres definiciones de propiedad: una para `TotalItems` y dos para `Item`, que está sobrecargado.  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 La propiedad `TotalItems` no requiere argumentos y se puede inicializar en una lista de inicialización de objetos, tal como se muestra en la siguiente declaración.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 La propiedad `Item` está sobrecargada y cada sobrecarga requiere un argumento. Por lo tanto, `Item` no puede aparecer en una lista de inicializadores de objeto.  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 Para evitar este error, inicialice la propiedad `Item` fuera del inicializador de objeto.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedad](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Cómo: Llamar a un procedimiento de propiedad](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades predeterminadas](http://msdn.microsoft.com/es-es/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)