---
title: "No hay un mouse presente. | Microsoft Docs"
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
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No hay un mouse presente.
Se llamó a una de las propiedades del objeto `My.Computer.Mouse`, pero el equipo no tiene ningún mouse o puerto de mouse instalado.  
  
### Para corregir este error  
  
-   Agregue un bloque `Try...Catch` alrededor de la llamada a la propiedad del objeto `My.Computer.Mouse`.  
  
     o  
  
-   Instale un mouse en el equipo.  
  
## Vea también  
 [My.Computer.Mouse \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-computer-mouse-object)   
 [Control de excepciones y errores en Visual Basic](http://msdn.microsoft.com/es-es/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)