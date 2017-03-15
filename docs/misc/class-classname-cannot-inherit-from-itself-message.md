---
title: "Clase &#39;&lt;classname&gt;&#39; no puede heredar de s&#237; misma: &lt;message&gt; | Microsoft Docs"
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
  - "vbc30257"
  - "bc30257"
helpviewer_keywords: 
  - "BC30257"
ms.assetid: 03e3034c-a0fa-4619-84b9-5bc9aa0dfe80
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Clase &#39;&lt;classname&gt;&#39; no puede heredar de s&#237; misma: &lt;message&gt;
Un elemento [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) en una clase definición especifica su propia clase.  
  
 Una clase puede heredar de otra clase, que le proporciona todos los miembros de la clase de la que hereda, por lo que no tiene que definir esos miembros de nuevo. Esta clase se denomina una *clase derivada* y la clase de la que hereda se conoce como *clase base*.  
  
 No tiene sentido que una clase herede de sí misma porque ya posee todos sus miembros.  
  
 **Id. de error:** BC30257  
  
### Para corregir este error  
  
1.  Compruebe que esté bien escrito el nombre de la clase en la instrucción `Inherits`.  
  
2.  Si no tiene intención de heredar de una clase diferente, quite por completo la instrucción `Inherits`.  
  
3.  Examine el mensaje citado para obtener sugerencias.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [NO ESTÁ EN LA COMPILACIÓN: Introducción a las clases](http://msdn.microsoft.com/es-es/cc2355a2-cb98-4353-9440-736585aec46c)