---
title: "Error del compilador CS1731 | Microsoft Docs"
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
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1731
No se puede convertir 'expresión' a delegado porque algunos de los tipos de valor devuelto del bloque no se pueden convertir implícitamente al tipo de valor devuelto del delegado.  
  
 Este error se genera cuando una expresión lambda o un método anónimo tiene un tipo de valor devuelto que no es compatible con el tipo de valor devuelto del delegado.  
  
### Para corregir este error  
  
1.  Cambie el tipo de valor devuelto del delegado o la expresión.  
  
## Ejemplo  
 El código siguiente genera el error CS1731.  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```