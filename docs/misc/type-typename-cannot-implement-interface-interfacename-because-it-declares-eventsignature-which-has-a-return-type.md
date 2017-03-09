---
title: "El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede implementar la interfaz &#39;&lt;nombreDeInterfaz&gt;&#39; porque declara &#39;&lt;signaturaDeEvento&gt;&#39;, que tiene un tipo de valor devuelto | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede implementar la interfaz &#39;&lt;nombreDeInterfaz&gt;&#39; porque declara &#39;&lt;signaturaDeEvento&gt;&#39;, que tiene un tipo de valor devuelto
Una clase o estructura intenta implementar una interfaz que declara un evento que devuelve un valor.  
  
 Visual Basic no admite actualmente la declaración de eventos que devuelven valores.  
  
 **Identificador de error:** BC30945  
  
### Para corregir este error  
  
-   Quitar la instrucción `Implements` de la definición de clase o de estructura, o bien implemente una interfaz diferente.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Eventos y controladores de eventos](http://msdn.microsoft.com/es-es/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)