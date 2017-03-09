---
title: "Advertencia de conformidad con CLS CLS01701 | Microsoft Docs"
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
  - "CLS01701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01701"
ms.assetid: 6ccbe156-9017-44ea-bd4e-a838af2ec2e7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01701
Los tipos de puntero no administrados no son conformes a CLS.  
  
 Un constructor conforme a CLS no puede contener una declaración de puntero nativo.  
  
 Para información sobre la comprobación de conformidad con CLS, vea [Ensamblados compatibles con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01701:  
  
```  
// CLS01701.cpp // compile with: /clr /LD // CLS01701 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: One(int* Parameter) {}   // CLS01701 };  
```