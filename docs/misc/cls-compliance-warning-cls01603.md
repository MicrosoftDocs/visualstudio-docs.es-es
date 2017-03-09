---
title: "Advertencia de conformidad con CLS CLS01603 | Microsoft Docs"
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
  - "CLS01603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01603"
ms.assetid: 608ff6e6-8669-4cc7-a85f-5b6915ee38d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01603
Las matrices deben tener elementos con un tipo conforme a CLS y los límites inferiores de todas las dimensiones de la matriz deben ser iguales a cero  
  
 Las matrices deben tener elementos con un tipo conforme a CLS y los límites inferiores de todas las dimensiones de la matriz deben ser iguales a cero. Para distinguir entre sobrecargas, solo se tendrá en cuenta el hecho de que el elemento es una matriz y el tipo de elementos de la matriz. Cuando la sobrecarga se basa en dos o varios tipos de matrices, los tipos de elementos deben ser tipos con nombre.  
  
 Para obtener más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 El ejemplo siguiente genera la advertencia CLS01603:  
  
```  
// CLS01603.cpp // compile with: /clr /LD // CLS01603 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public delegate void MyDelegate(Object ^ sender, EventArgs^ e); public delegate void MyDelegate2(Object ^ sender, EventArgs^ e); public ref struct One { array<MyDelegate^>^ MyArray;   // CLS01603 array<MyDelegate2^>^ MyArray2;   // OK };  
```