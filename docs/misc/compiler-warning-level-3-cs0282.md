---
title: "Advertencia del compilador (nivel 3) CS0282 | Microsoft Docs"
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
  - "CS0282"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0282"
ms.assetid: fd4cda5d-81c7-40e3-8424-c938b3447356
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0282
No hay un orden específico entre los campos en declaraciones múltiples de 'tipo' de class o struct parciales. Para especificar un orden, todos los campos de instancia deben estar en la misma declaración.  
  
 Para resolver este error, coloque todas las variables de miembro en una definición de class parcial única.  
  
 Una manera habitual de recibir este error es cuando se define una `struct` parcial en más de un lugar, con algunas de las variables de miembro en una definición y otras en otro.  
  
 El código siguiente genera la advertencia CS0282:  
  
## Ejemplo  
 Este código contiene una descripción de una `struct`. Compile estos dos módulos juntos en un solo paso mediante el comando:  
  
 `csc /targt:library cs0282_1.cs cs0282_2.cs`  
  
```  
partial struct A { int i; }  
```  
  
## Ejemplo  
 Este código contiene una descripción en conflicto de la misma `struct`.  
  
```  
partial struct A { int j; }  
```