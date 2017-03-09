---
title: "Hay varias inicializaciones de &#39;&lt;nombreMiembro&gt;&#39;. | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Hay varias inicializaciones de &#39;&lt;nombreMiembro&gt;&#39;.
Hay varias inicializaciones de '\<nombreMiembro\>'. Los campos y las propiedades solo se pueden inicializar una vez en una expresión de inicializador de objeto.  
  
 Puede asignar un valor inicial a cada campo y propiedad en una lista de inicializadores de objeto solo una vez. La siguiente declaración no es válida.  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  Puede usar un campo o propiedad como valor inicial para otro miembro, como se muestra en la siguiente declaración.  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **Identificador de error:** BC30989  
  
### Para corregir este error  
  
-   Elimine todas las inicializaciones excepto una para cada campo o propiedad en la lista de inicializadores de objeto.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimientos de propiedad frente a Campos](http://msdn.microsoft.com/es-es/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)