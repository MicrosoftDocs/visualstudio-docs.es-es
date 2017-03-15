---
title: "Las instrucciones &#39;On Error&#39; no son v&#225;lidas dentro de instrucciones &#39;Using&#39; | Microsoft Docs"
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
  - "vbc36013"
  - "bc36013"
helpviewer_keywords: 
  - "BC36013"
ms.assetid: 5b399bf9-6595-46e0-a808-378f6c28568b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;On Error&#39; no son v&#225;lidas dentro de instrucciones &#39;Using&#39;
Una instrucción `On Error` aparece dentro de una instrucción `Using`, pero no es válida en ese contexto.  
  
 **Identificador de error:** BC36013  
  
### Para corregir este error  
  
-   Use el control de errores estructurado, como un bloque `Try…Catch`, en lugar de la instrucción `On Error`.  
  
## Vea también  
 [Información general sobre el control estructurado de excepciones de Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)   
 [Elegir cuándo se debe usar el control estructurado de excepciones y cuándo el control no estructurado de excepciones \(Visual Basic\)](http://msdn.microsoft.com/es-es/e897d7ca-07e8-45dd-8a6d-a5b2a2fc9b9a)   
 [On Error \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/on-error-statement)   
 [Cómo: Probar el código con un bloque Try...Catch en Visual Basic](http://msdn.microsoft.com/es-es/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)