---
title: "No se puede inicializar la propiedad &#39;&lt;propertyname&gt;&#39; en una expresi&#243;n de inicializador de objeto porque requiere argumentos | Microsoft Docs"
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
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inicializar la propiedad &#39;&lt;propertyname&gt;&#39; en una expresi&#243;n de inicializador de objeto porque requiere argumentos
Los miembros inicializados de la lista de inicializadores de objeto deben ser campos o propiedades y los miembros de la propiedad no pueden tener parámetros. Por ejemplo, las propiedades predeterminadas requieren argumentos, por lo que no se pueden inicializar en una lista de inicializadores de objeto. Para más información, vea [NO ESTÁ EN LA COMPILACIÓN: Propiedades predeterminadas](http://msdn.microsoft.com/es-es/a70f2a27-8176-4858-935e-f25afdd43ab5).  
  
 **Identificador de error:** BC30992  
  
### Para corregir este error  
  
-   Quite de la lista de inicialización todas las propiedades que tienen argumentos.  
  
## Ejemplo  
 La clase siguiente contiene una propiedad predeterminada, `defaultProp`, que requiere un argumento entero.  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 Dado que la propiedad predeterminada requiere un argumento, la siguiente declaración genera un error.  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades predeterminadas](http://msdn.microsoft.com/es-es/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedades](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)