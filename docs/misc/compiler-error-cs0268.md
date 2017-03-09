---
title: "Error del compilador CS0268 | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0268
El tipo importado 'type' no es válido. Contiene una dependencia de clase base circular.  
  
 Este error se produce si un tipo importado de otro lenguaje tiene una dependencia de clase base circular. Este tipo no se puede usar en un programa de C\#. Para resolver este error, compruebe los tipos importados de otros lenguajes en los ensamblados de referencia o módulos.