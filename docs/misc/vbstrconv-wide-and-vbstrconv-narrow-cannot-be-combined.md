---
title: "No se pueden combinar VbStrConv.Wide y VbStrConv.Narrow | Microsoft Docs"
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
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden combinar VbStrConv.Wide y VbStrConv.Narrow
La aplicación está intentando combinar los miembros de la enumeración `VbStrConv``Wide` y `Narrow`, que son mutuamente excluyentes.  
  
### Para corregir este error  
  
1.  Quite `VbStrConv.Wide` o `VbStrConv.Narrow`.  
  
## Vea también  
 <xref:System.Globalization>   
 [NOTINBUILD Enumeración VbStrConv](http://msdn.microsoft.com/es-es/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)