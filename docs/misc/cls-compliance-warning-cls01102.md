---
title: "Advertencia de conformidad con CLS CLS01102 | Microsoft Docs"
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
  - "CLS01102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01102"
ms.assetid: 49426c42-9d01-49ba-b061-ca0e8bd6782d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01102
Todos los tipos que aparecen en una signatura deben ser conformes a CLS.  
  
 Si el evento es conforme a CLS, todos los tipos usados en las funciones de acceso del evento, salvo que estén marcados como no conformes a CLS, deben ser tipos conformes a CLS.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93) \(Ensamblados conformes a CLS\).  
  
```  
// CLS01102.cpp // compile with: /clr /LD // CLS01102 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; // Test types [CLSCompliant(true)] public delegate void CompliantType([parameter:CLSCompliant(true)] int parameter); [CLSCompliant(false)] public delegate void NotCompliantType([parameter:CLSCompliant(false)] int parameter); public ref class One { public: event NotCompliantType^ MyEvent { public: void add(NotCompliantType^ Addparameter) {} void remove(NotCompliantType^ Removeparameter) {} void raise([parameter:CLSCompliant(false)] int parameter) {} } };  
```