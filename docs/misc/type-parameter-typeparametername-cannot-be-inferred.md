---
title: "No se puede inferir el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39;
Se llama a un procedimiento genérico sin proporcionar una lista de argumentos de tipo y se produce un error en la inferencia de tipos para uno de los argumentos de tipo.  
  
 Cuando se llama a un procedimiento genérico, normalmente se proporciona un argumento de tipo para cada parámetro de tipo definido por el procedimiento. Sin embargo, tiene la alternativa de omitir completamente la lista de argumentos de tipo. Al hacerlo, el compilador intenta inferir el tipo de cada argumento de tipo a partir del contexto de la llamada. Para obtener más información, vea "Inferencia de tipos" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Identificador de error:** BC36572  
  
### Para corregir este error  
  
-   Asegúrese de que los tipos de los argumentos normales son tales que la inferencia de tipo es coherente con los parámetros de tipo declarados para el procedimiento genérico.  
  
     O bien  
  
-   Llame al procedimiento genérico con una lista completa de argumentos de tipo para que no sea necesaria la inferencia de tipos.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)