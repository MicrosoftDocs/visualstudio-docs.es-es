---
title: "Advertencia de conformidad con CLS CLS04106 | Microsoft Docs"
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
  - "CLS04106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04106"
ms.assetid: a74e4cb7-c96a-4673-bf11-c2ff3c4b02f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS04106
Los atributos deben ser del tipo 'System::Attribute' o heredarse de dicho atributo  
  
 Para ser conforme a CLS, un atributo personalizado debe heredarse de System::Attribute.  Un atributo que no se heredó de System::Attribute se aplicó a una función.  
  
 La siguiente declaración \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar CLS04106:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 y, a continuación, una función que usa el atributo:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Hacer que el atributo se derive de System::Attribute resuelve la advertencia:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```