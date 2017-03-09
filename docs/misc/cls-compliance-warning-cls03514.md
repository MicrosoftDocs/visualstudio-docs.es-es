---
title: "Advertencia de conformidad con CLS CLS03514 | Microsoft Docs"
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
  - "CLS03514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03514"
ms.assetid: b2d326ce-8c1b-4351-80d1-ccd1818b1ea3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS03514
CLS no permite modificadores obligatorios que sean visibles públicamente \(modreq\), pero sí permite modificadores opcionales \(modopt\) que no comprenden.  
  
 CLS no permite modificadores obligatorios que sean visibles públicamente \(modreq\), pero sí permite modificadores opcionales \(modopt\) que no comprenden.  
  
 Asegúrese de que las signaturas de método no contienen tipos marcados con modificadores obligatorios que sean visibles públicamente.  
  
 Para más información sobre la comprobación de conformidad con Common Language Subset \(CLS\), vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS03514:  
  
```  
// CLS03514.cpp // compile with: /clr /LD // CLS03514 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDel(volatile Int32 param);   // CLS03514 public delegate void MyDel2(Int32 param);   // OK  
```