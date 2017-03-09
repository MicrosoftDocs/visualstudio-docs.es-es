---
title: "El nombre del campo o la propiedad que se est&#225; inicializando debe comenzar por &#39;.&#39; | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre del campo o la propiedad que se est&#225; inicializando debe comenzar por &#39;.&#39;
Cada inicializador de miembro de una lista de inicializadores de objeto especifica el nombre de un campo o una propiedad y su valor inicial. El nombre del campo o la propiedad debe ir precedido de un punto. Por ejemplo, la siguiente declaración asigna "Microsoft" como valor inicial de la propiedad `Name` de `client`.  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **Identificador de error:** BC30985  
  
### Para corregir este error  
  
-   Prefije cada nombre de miembro con un punto.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Comparación de procedimientos de propiedades y Campos](http://msdn.microsoft.com/es-es/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)