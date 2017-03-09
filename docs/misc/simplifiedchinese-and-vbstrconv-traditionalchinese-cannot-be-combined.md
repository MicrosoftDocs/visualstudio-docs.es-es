---
title: "No se pueden combinar SimplifiedChinese y VbStrConv.TraditionalChinese | Microsoft Docs"
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
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden combinar SimplifiedChinese y VbStrConv.TraditionalChinese
La aplicación está intentando combinar los `VbStrConv` miembros de la enumeración `SimplifiedChinese` y `TraditionalChinese`, que son mutuamente excluyentes.  
  
### Para corregir este error  
  
-   Quite  `VbStrConv.SimplifiedChinese` o `VbStrConv.TraditionalChinese`.  
  
## Vea también  
 <xref:System.Globalization>   
 [NOTINBUILD: Enumeración VbStrConv](http://msdn.microsoft.com/es-es/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)