---
title: "&#39;End Get&#39; debe ir precedida de la instrucci&#243;n &#39;Get&#39; correspondiente | Microsoft Docs"
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
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Get&#39; debe ir precedida de la instrucci&#243;n &#39;Get&#39; correspondiente
`End Get` se usa para finalizar los procedimientos de la propiedad `Get`. Se encontró la construcción `End Get` fuera del procedimiento de la propiedad `Get`.  
  
 **Identificador de error:** BC30630  
  
### Para corregir este error  
  
1.  Asegúrese de que el procedimiento de la propiedad `Get` se declare después de la palabra clave `Property` y antes de la construcción `End Property`.  
  
2.  Asegúrese de que el procedimiento de la propiedad `Get` comience con la palabra clave `Get` y finalice con la construcción `End Get`.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/es-es/1c138efa-9bc2-44d7-80a0-f3a7c2510264)