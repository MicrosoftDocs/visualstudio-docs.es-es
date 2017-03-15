---
title: "No se puede inicializar el miembro &#39;&lt;membername&gt;&#39; en una expresi&#243;n de inicializador de objeto porque no es un campo ni una propiedad. | Microsoft Docs"
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
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inicializar el miembro &#39;&lt;membername&gt;&#39; en una expresi&#243;n de inicializador de objeto porque no es un campo ni una propiedad.
Una lista de inicializadores de objeto no puede incluir miembros compartidos, constantes ni llamadas a métodos. Los miembros de la lista de inicializadores deben ser campos o propiedades, y los miembros de la propiedad no pueden requerir argumentos.  
  
 **Identificador de error:** BC30990  
  
### Para corregir este error  
  
-   Quite de la lista de inicializadores de objetos todos los miembros compartidos, constantes, llamadas a métodos o propiedades que tengan parámetros.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Miembros compartidos en Visual Basic](http://msdn.microsoft.com/es-es/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedad](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades predeterminadas](http://msdn.microsoft.com/es-es/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [No está en la compilación: Miembros de objetos](http://msdn.microsoft.com/es-es/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Const \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/const-statement)