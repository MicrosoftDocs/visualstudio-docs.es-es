---
title: "Advertencia del compilador (nivel 1) CS1697 | Microsoft Docs"
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
  - "CS1697"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1697"
ms.assetid: 0cd931b7-f358-4ff0-b441-27668645d7d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1697
Se han proporcionado distintos valores de suma de comprobación para 'file name'  
  
 Ha especificado más de una suma de comprobación para un archivo determinado. El depurador usa el valor de suma de comprobación para determinar qué archivo debe depurar cuando hay más de un archivo en un proyecto con el mismo nombre. La mayoría de los usuarios no encontrará este error, pero si está escribiendo una aplicación que genera código, puede encontrárselo. Para resolver este error, asegúrese de que genera la suma de comprobación solo una vez para cualquier archivo de código determinado.