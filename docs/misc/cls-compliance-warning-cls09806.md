---
title: "Advertencia de conformidad con CLS CLS09806 | Microsoft Docs"
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
  - "CLS09806"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS09806"
ms.assetid: fc97cf0e-c72e-4c09-96be-f90f9840e76e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS09806
Los métodos genéricos no son conformes a CLS.  
  
 Un método genérico no es conforme a CLS.  
  
 Para más información sobre la comprobación de conformidad con Common Language Subset \(CLS\), vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS09806:  
  
```  
// CLS09806.cpp // compile with: /clr /LD /link /noentry // CLS09806 expected using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; using namespace System; [assembly:CLSCompliant (true)]; generic <class T> public ref struct One { public: generic <class U> void Method1() {} };  
```