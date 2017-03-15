---
title: "Advertencia de conformidad con CLS CLS00911 | Microsoft Docs"
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
  - "CLS00911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00911"
ms.assetid: d1a4721a-a3a6-4de0-bc14-a0b3c5e6dd78
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS00911
Los campos estáticos literales de una enumeración deben contener el tipo de la propia enumeración  
  
 Asegúrese de que los campos estáticos literales de una enumeración tengan el tipo de la propia enumeración.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados conformes con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar el error CLS00911:  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal uint8 One = uint8(0x1) } // end of class MyEnum1 }  
```  
  
 Si hace que el campo enum sea de tipo enum, puede resolver esta advertencia:  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal valuetype Test.MyEnum1 One = uint8(0x1) } // end of class MyEnum1 }  
```