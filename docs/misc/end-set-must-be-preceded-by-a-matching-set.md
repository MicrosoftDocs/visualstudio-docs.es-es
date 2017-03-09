---
title: "&#39;End Set&#39; debe ir precedida de la instrucci&#243;n &#39;Set&#39; correspondiente | Microsoft Docs"
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
  - "bc30632"
  - "vbc30632"
helpviewer_keywords: 
  - "BC30632"
ms.assetid: 0c3dd065-566b-485c-9996-6177eb0fde39
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Set&#39; debe ir precedida de la instrucci&#243;n &#39;Set&#39; correspondiente
`End Set` se usa para finalizar los procedimientos de la propiedad `Set`. Se encontró la construcción `End Set` fuera del procedimiento de la propiedad `Set`.  
  
 **Identificador de error:** BC30632  
  
### Para corregir este error  
  
1.  Asegúrese de que el procedimiento de la propiedad `Set` se declare después de la palabra clave `Property` y antes de la construcción `End Property`.  
  
2.  Asegúrese de que el procedimiento de la propiedad `Set` comience con la palabra clave `Set` y finalice con la construcción `End Set`.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/es-es/1c138efa-9bc2-44d7-80a0-f3a7c2510264)