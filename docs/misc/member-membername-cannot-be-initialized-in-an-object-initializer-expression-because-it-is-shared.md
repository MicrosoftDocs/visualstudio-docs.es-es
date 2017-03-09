---
title: "No se puede inicializar el miembro &#39;&lt;nombreMiembro&gt;&#39; en una expresi&#243;n de inicializador de objeto porque est&#225; compartido. | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inicializar el miembro &#39;&lt;nombreMiembro&gt;&#39; en una expresi&#243;n de inicializador de objeto porque est&#225; compartido.
Los inicializadores de objeto no se pueden usar para inicializar un miembro de una clase que se declara como compartida. Para obtener más información, consulta [Shared](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 **Identificador de error:** BC30991  
  
### Para corregir este error  
  
1.  Examine la definición de clase para determinar qué miembros se comparten.  
  
2.  Elimine la inicialización para ese miembro de la lista de inicializadores de objeto.  
  
## Ejemplo  
 En el ejemplo siguiente, `totalCustomers` es un miembro compartido.  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 Como `totalCustomers` es compartido, al intentar establecer su valor inicial de una lista de inicializadores de objeto se genera este error.  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NO ESTÁ EN LA COMPILACIÓN: Miembros compartidos en Visual Basic](http://msdn.microsoft.com/es-es/dbc3783f-83a2-4225-995d-c2d6d025663d)