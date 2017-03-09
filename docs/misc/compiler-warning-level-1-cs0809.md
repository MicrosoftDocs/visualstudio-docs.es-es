---
title: "Advertencia del compilador (nivel 1) CS0809 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0809
El miembro obsoleto 'miembroA' reemplaza al miembro no obsoleto 'miembroB'.  
  
 Normalmente, un miembro marcado como obsoleto no debe reemplazar a un miembro que no está marcado como obsoleto. Esta advertencia se genera en [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], pero no en [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Para corregir este error  
  
1.  Quite el atributo `Obsolete` del miembro de reemplazo o agréguelo al miembro de clase base.  
  
## Ejemplo  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```