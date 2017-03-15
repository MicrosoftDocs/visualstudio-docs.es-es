---
title: "&#39;Catch&#39; no puede poner al d&#237;a el tipo &#39;&lt;nombreDeTipo&gt;&#39; porque no es &#39;System.Exception&#39; ni una clase que hereda de &#39;System.Exception&#39; | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; no puede poner al d&#237;a el tipo &#39;&lt;nombreDeTipo&gt;&#39; porque no es &#39;System.Exception&#39; ni una clase que hereda de &#39;System.Exception&#39;
`Catch` solo puede interceptar excepciones e intentó poner al día algo que no se deriva de una excepción.  
  
 **Identificador de error:** BC30392  
  
### Para corregir este error  
  
1.  Quite la instrucción `Catch` o cambie el destino de `Catch` a una excepción real.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general sobre el control estructurado de excepciones de Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)