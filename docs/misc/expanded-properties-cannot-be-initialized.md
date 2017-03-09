---
title: "Las propiedades expandidas no se pueden inicializar | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las propiedades expandidas no se pueden inicializar
Se puede inicializar una propiedad implementada automáticamente como parte de su declaración, pero no una propiedad expandida.  
  
 **Identificador de error:** BC36714  
  
### Para corregir este error  
  
-   Use una propiedad implementada automáticamente o quite la inicialización de la declaración de propiedad.  
  
## Ejemplo  
 Los ejemplos siguientes muestran propiedades implementadas automáticamente y propiedades expandidas. Se pueden inicializar propiedades implementadas automáticamente mediante la asignación o una cláusula `New`, pero no propiedades expandidas.  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## Vea también  
 [Propiedades autoimplementadas](/dotnet/visual-basic/programming-guide/language-features/procedures/auto-implemented-properties)   
 [Cómo: Crear una propiedad](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)