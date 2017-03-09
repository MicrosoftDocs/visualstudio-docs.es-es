---
title: "Advertencia de conformidad con CLS CLS01106 | Microsoft Docs"
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
  - "CLS01106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01106"
ms.assetid: 0c964444-387d-4348-aed5-05f1ccc241c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01106
**Todos los tipos que aparecen en una signatura deben ser conformes a CLS**  
  
 Si un tipo es conforme a CLS, todas las funciones del tipo, a menos que estén marcadas como no conformes a CLS, deben tener parámetros de tipo conformes a CLS.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01106:  
  
```  
// CLS01106.cpp // compile with: /clr /LD // CLS01106 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; [CLSCompliant(true)] public ref class One { public: NotCompliantType^ Method1(NotCompliantType^ parameter) { return parameter; } CompliantType^ Method2(CompliantType^ parameter) {   // OK return parameter; } [CLSCompliant(false)] NotCompliantType^ Method3(NotCompliantType^ parameter) {   // OK return parameter; } };  
```