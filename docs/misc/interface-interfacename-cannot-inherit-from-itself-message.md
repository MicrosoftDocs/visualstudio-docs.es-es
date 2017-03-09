---
title: "La interfaz &#39;&lt;interfacename&gt;&#39; no puede heredar de s&#237; misma: &lt;mensaje&gt; | Microsoft Docs"
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
  - "vbc30296"
  - "BC30296"
helpviewer_keywords: 
  - "BC30296"
ms.assetid: a5bc1ae2-2083-4e26-b8a4-3c4dd951fd27
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La interfaz &#39;&lt;interfacename&gt;&#39; no puede heredar de s&#237; misma: &lt;mensaje&gt;
[Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) en una definición de interfaz especifica su propia interfaz.  
  
 Una interfaz puede heredar de otra interfaz, que le proporciona todos los miembros de la interfaz de la que hereda, por lo que no tiene que definir esos miembros de nuevo. Dicha interfaz se denomina *interfaz derivada* y se llama a la interfaz de la que hereda, que se denomina  *interfaz base*.  
  
 No tiene sentido que una interfaz herede de sí misma porque ya posee todos sus miembros.  
  
 **Identificador de error:** BC30296  
  
### Para corregir este error  
  
1.  Compruebe que esté bien escrito el nombre de la interfaz en la instrucción `Inherits`.  
  
2.  Si no tiene intención de heredar de una interfaz diferente, quite por completo la instrucción `Inherits`.  
  
3.  Examine el mensaje citado para obtener sugerencias.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)