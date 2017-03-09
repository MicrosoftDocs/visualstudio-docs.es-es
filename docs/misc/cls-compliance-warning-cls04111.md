---
title: "Advertencia de conformidad con CLS CLS04111 | Microsoft Docs"
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
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS04111
Los atributos deben ser del tipo 'System::Attribute' o heredarse de este  
  
 Para ser conforme a CLS, un atributo personalizado debe heredarse de System::Attribute.  Un atributo que no se heredó de System::Attribute se aplicó a un tipo.  
  
 La siguiente declaración \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar la advertencia CLS04111:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Hacer que el atributo se derive de System::Attribute resuelve la advertencia:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```