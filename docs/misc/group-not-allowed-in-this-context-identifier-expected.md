---
title: "No se permite &#39;Group&#39; en este contexto; se esperaba un identificador | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite &#39;Group&#39; en este contexto; se esperaba un identificador
La palabra clave `Group` se incluye en la sección `Into` de un cláusula `Aggregate`. La palabra clave `Group` solo es válido en las cláusulas `Group By` o `Group Join`.  
  
 **Identificador de error:** BC36618  
  
### Para corregir este error  
  
-   Quite la palabra clave `Group` de la cláusula `Aggregate`. Puede agregar una cláusula `Group By` a la consulta para agrupar los resultados.  
  
## Vea también  
 [Aggregate \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Group By \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)