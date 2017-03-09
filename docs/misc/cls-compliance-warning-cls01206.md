---
title: "Advertencia de conformidad con CLS CLS01206 | Microsoft Docs"
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
  - "CLS01206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01206"
ms.assetid: e72f2293-874b-406c-9f22-92aeb64ac732
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01206
La visibilidad y accesibilidad de los tipos y miembros se establecerá de modo que los tipos de la signatura de cualquier miembro sean visibles y accesibles siempre que el propio miembro sea visible y accesible. Por ejemplo, una función de miembro público que sea visible fuera del ensamblado no debe tener ningún argumento cuyo tipo solamente sea visible dentro del ensamblado.  
  
 Los tipos de las signaturas de método deben tener una accesibilidad mayor o igual que la del método.  Por ejemplo, un método público que sea visible fuera del ensamblado no debe tener ningún argumento cuyo tipo solamente sea visible en el interior del ensamblado.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01206:  
  
```  
/* CLS01206.cpp */ // compile with: /clr /LD // CLS01206 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Method1() { return gcnew AssemblyLevelType(); } };  
```