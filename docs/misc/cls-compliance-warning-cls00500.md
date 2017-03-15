---
title: "Advertencia de conformidad con CLS CLS00500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS00500
Todos los nombres en un ámbito conforme a CLS deben ser distintos independientemente del tipo  
  
 Todos los nombres especificados en un ámbito conforme a CLS deben ser distintos independientemente del tipo, salvo en los casos en los que los nombres sean idénticos y se resuelvan mediante sobrecarga. Para CLS, dos nombres son el mismo si sus asignaciones de minúsculas son iguales. Solo las propiedades y los métodos se pueden sobrecargar. En caso de sobrecargarse, las propiedades y las funciones solo deberán estarlo según el número y el tipo de sus parámetros, excepto los operadores de conversión, que también pueden sobrecargarse según el tipo de valor devuelto; vea [Conversiones definidas por el usuario](/visual-cpp/dotnet/user-defined-conversions-cpp-cli) para más información.  
  
 Para más información sobre la comprobación de la conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93) \(Ensamblados conformes a CLS\).  
  
 El ejemplo siguiente genera la advertencia CLS00500:  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```