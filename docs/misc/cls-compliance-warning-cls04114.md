---
title: "Advertencia de conformidad con CLS CLS04114 | Microsoft Docs"
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
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS04114
Los atributos deben ser del tipo 'System::Attribute' o heredarse de este  
  
 Para ser conforme a CLS, un atributo personalizado debe heredarse de System::Attribute.  Un atributo que no se heredó de System::Attribute se aplicó a un delegado.  
  
 Para más información sobre la comprobación de conformidad con Common Language Subset \(CLS\), vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93) \(Ensamblados conformes a CLS\).  
  
 La siguiente declaración \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar CLS04100:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 y, después, un delegado que usa el atributo:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Hacer que el atributo se derive de System::Attribute resuelve la advertencia:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```