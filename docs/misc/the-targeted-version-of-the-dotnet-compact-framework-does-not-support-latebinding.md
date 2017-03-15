---
title: "La versi&#243;n de destino de .NET Compact Framework no admite enlaces en tiempo de ejecuci&#243;n. | Microsoft Docs"
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
  - "vbc30762"
  - "bc30762"
helpviewer_keywords: 
  - "BC30762"
ms.assetid: b433014d-8422-46e8-ad55-321146a48186
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La versi&#243;n de destino de .NET Compact Framework no admite enlaces en tiempo de ejecuci&#243;n.
La versión de .NET Compact Framework con la que está trabajando no admite enlaces en tiempo de ejecución.  
  
 **Identificador de error:** BC30762  
  
### Para corregir este error  
  
1.  Evite llamar a funciones, subrutinas o propiedades en una variable declarada como objeto.  
  
2.  Evite usar la variable de objeto como una matriz.  
  
3.  Evite usar expresiones de acceso a miembros de diccionario con variables de objeto.  
  
## Vea también  
 [No está en la compilación:Objetos en Visual Basic](http://msdn.microsoft.com/es-es/85bd757a-a19e-45e1-af89-d68765f5ee3c)   
 [Caracteres especiales en código](/dotnet/visual-basic/programming-guide/program-structure/special-characters-in-code)