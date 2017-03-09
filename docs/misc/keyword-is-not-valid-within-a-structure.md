---
title: "&#39;palabra clave&#39; no es v&#225;lida dentro de una estructura. | Microsoft Docs"
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
  - "bc30044"
  - "vbc30044"
helpviewer_keywords: 
  - "BC30044"
ms.assetid: 252510cf-e084-47e4-9592-4aa8f94fabe4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;palabra clave&#39; no es v&#225;lida dentro de una estructura.
Las estructuras son tipos de valor, no tipos de referencia. Una estructura no es una instancia creada a partir de una clase, por lo que las palabras clave `Me`, `MyClass` y `MyBase` no tienen sentido en una estructura.  
  
 **Identificador de error:** BC30044  
  
### Para corregir este error  
  
-   Cambie la estructura a una clase o quite la palabra clave del procedimiento.  
  
## Vea también  
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass: eliminar](http://msdn.microsoft.com/es-es/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [MyBase: eliminar](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)