---
title: "Advertencia del compilador (nivel 2) CS0444 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0444
El tipo predefinido 'nombre de tipo 1' no se encontró en 'espacio de nombres System 1', pero sí en 'espacio de nombres System 2'  
  
 No se encontró un objeto predefinido como <xref:System.Int32> donde el compilador esperaba, pero sí en 'espacio de nombres System 2'.  
  
 El error puede indicar que .NET Framework está instalado incorrectamente. Para solucionar este problema, reinstale .NET Framework.  
  
 Si escribe sus propias bibliotecas de clase base, también se podría producir este error. En este caso, vuelva a generar mscorlib para resolverlo.