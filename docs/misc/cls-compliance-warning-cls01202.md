---
title: "Advertencia de conformidad con CLS CLS01202 | Microsoft Docs"
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
  - "CLS01202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01202"
ms.assetid: ab75e9c4-9d87-4bb4-ad8f-3e6ab5559de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01202
La visibilidad y accesibilidad de los tipos y miembros se establecerá de modo que los tipos de la signatura de cualquier miembro sean visibles y accesibles siempre que el propio miembro sea visible y accesible. Por ejemplo, un evento público que sea visible fuera del ensamblado no debe tener ningún argumento cuyo tipo solamente sea visible en el interior del ensamblado.  
  
 El tipo de un controlador de eventos debe tener una accesibilidad mayor o igual que la accesibilidad del controlador de eventos.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados compatibles con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01202:  
  
```  
/* CLS01202.cpp */ // compile with: /clr /LD // CLS01202 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyPublicDelegate(); private delegate void MyAssemblyDelegate(); public ref class One { public: event MyAssemblyDelegate^ MyEvent { public: void add(MyAssemblyDelegate^ Addparameter) {}   //  not cls compliant void remove(MyAssemblyDelegate^ Removeparameter) {}   //  not cls compliant void raise() {} } };  
```