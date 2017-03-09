---
title: "Advertencia de conformidad con CLS CLS01214 | Microsoft Docs"
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
  - "CLS01214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01214"
ms.assetid: 5968af20-3d3e-4c7b-ad61-c06979cc9efd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01214
La visibilidad y accesibilidad de los tipos y miembros se establecerá de modo que los tipos de la signatura de cualquier miembro sean visibles y accesibles siempre que el propio miembro sea visible y accesible. Por ejemplo, un delegado que sea visible fuera del ensamblado no debe tener ningún argumento cuyo tipo solamente sea visible en el interior del ensamblado.  
  
 Los tipos de las signaturas de delegado deben tener una accesibilidad superior o igual a la del delegado.  Por ejemplo, un delegado que sea visible fuera del ensamblado no debe tener ningún argumento cuyo tipo solamente sea visible en el interior del ensamblado.  
  
 Para obtener más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01214:  
  
```  
/* CLS01214.cpp */ // compile with: /clr /LD // CLS01214 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicType {}; private ref class AssemblyType {}; public delegate PublicType^ AssemblyDelegate(AssemblyType^ parameter);   // not cls compliant public delegate PublicType^ AssemblyDelegate2(PublicType^ parameter);   //cls compliant  
```