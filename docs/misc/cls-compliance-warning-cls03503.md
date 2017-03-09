---
title: "Advertencia de conformidad con CLS CLS03503 | Microsoft Docs"
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
  - "CLS03503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03503"
ms.assetid: 2d2e78db-5fcf-47e1-af1e-9545f28a306b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS03503
CLS no permite modificadores obligatorios que sean visibles públicamente \(modreq\), pero sí permite modificadores opcionales \(modopt\) que no comprende  
  
 CLS no permite modificadores obligatorios que sean visibles públicamente \(modreq\), pero sí permite modificadores opcionales \(modopt\) que no comprende.  
  
 Asegúrese de que los campos no contienen tipos marcados con modificadores obligatorios que sean visibles públicamente.  
  
 Para obtener más información sobre la comprobación de conformidad con Common Language Subset \(CLS\), vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS03503:  
  
```  
// CLS03503.cpp // compile with: /clr /LD // CLS03503 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: volatile Int32 param;   // CLS03503 Int32 param2;   // OK };  
```