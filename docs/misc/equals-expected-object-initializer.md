---
title: "Se esperaba &#39;=&#39; (inicializador de objeto) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;=&#39; (inicializador de objeto)
Para establecer el valor inicial de un campo o una propiedad en una declaración de inicializador de objeto, se debe usar un signo igual. Por ejemplo, la siguiente declaración asigna "Microsoft" como valor inicial de la propiedad `Name` de `client`.  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **Identificador de error:** BC30984  
  
### Para corregir este error  
  
-   Agregue un signo igual en la posición que se muestra en el ejemplo anterior.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedad](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NO ESTÁ EN LA COMPILACIÓN: Comparación de procedimientos de propiedades y campos](http://msdn.microsoft.com/es-es/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)