---
title: "Advertencia de conformidad con CLS CLS01601 | Microsoft Docs"
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
  - "CLS01601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01601"
ms.assetid: fa162fc6-a0fd-4a0f-a201-4f166304d057
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01601
Las matrices deben tener elementos con un tipo conforme a CLS y los límites inferiores de todas las dimensiones de la matriz deben ser iguales a cero  
  
 Las matrices deben tener elementos con un tipo conforme a CLS y los límites inferiores de todas las dimensiones de la matriz deben ser iguales a cero. Para distinguir entre sobrecargas, solo se tendrá en cuenta el hecho de que el elemento es una matriz y el tipo de elementos de la matriz. Cuando la sobrecarga se basa en dos o varios tipos de matrices, los tipos de elementos deben ser tipos con nombre.  
  
 Para más información sobre la comprobación de la conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93) \(Ensamblados conformes a CLS\).  
  
 El ejemplo siguiente genera la advertencia CLS01601:  
  
```  
// CLS01601.cpp // compile with: /clr /LD // CLS01601 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01601 One(array<NotCompliantType^>^ param) {} // OK One(array<CompliantType^>^ param) {} };  
```