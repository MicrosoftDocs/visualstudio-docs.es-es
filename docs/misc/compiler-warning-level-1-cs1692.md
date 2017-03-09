---
title: "Advertencia del compilador (nivel 1) CS1692 | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1692
Número no válido  
  
 Varias directivas de preprocesador, como `#pragma` y `#line`, usan números como parámetros. Uno de estos números no es válido porque es demasiado grande, tiene un formato incorrecto, contiene caracteres no válidos, etc. Para resolver este error, corrija el número.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS1692.  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```