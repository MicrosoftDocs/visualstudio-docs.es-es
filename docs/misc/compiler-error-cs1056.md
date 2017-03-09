---
title: "Error del compilador CS1056 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1056"
ms.assetid: bf66d164-ab5b-4181-b93e-a1d29620b4d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1056
No se esperaba el carácter 'carácter'  
  
 El compilador de C\# encontró un carácter inesperado y no puede identificar el token que se está procesando actualmente. Por ejemplo, si el compilador encuentra un carácter de euro durante el procesamiento de un identificador, no podrá clasificar el identificador, ya que un carácter de euro solo sería válido dentro de una cadena y el compilador sabe que no está procesando una cadena.