---
title: "Se esperaba &#39;{&#39; | Microsoft Docs"
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
  - "vbc30987"
  - "bc30987"
helpviewer_keywords: 
  - "BC30987"
ms.assetid: 3d1552b6-338a-47cf-84d5-77b59209e0d3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;{&#39;
Para declarar una instancia de un tipo con nombre o anónimo usando un inicializador de objeto, debe incluir la lista de campos o propiedades y sus valores iniciales entre llaves \({ y }\).  
  
```  
Dim client As New Customer() With {.Name = "Microsoft", .City = "Seattle"}  
Dim emp = New Employee() With {.Name = "Rob Young", .ID = 55555}  
Dim anon = New With {.ID = 123456}  
```  
  
 **Identificador de error:** BC30987  
  
### Para corregir este error  
  
-   Incluya una lista de inicializaciones después de `With`, encerradas entre llaves.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimientos de propiedad frente a Campos](http://msdn.microsoft.com/es-es/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)   
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)