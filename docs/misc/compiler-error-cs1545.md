---
title: "Error del compilador CS1545 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1545"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1545"
ms.assetid: 56c377b5-4cf1-4c7d-b51d-463bad78f3ef
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1545
El lenguaje no admite la 'propiedad' de la propiedad, el indexador o el evento; intente llamar directamente a los métodos de descriptor de acceso 'set accessor' o 'get accessor'.  
  
 El código usa un objeto que tiene un [indexador](/dotnet/csharp/programming-guide/indexers/index) no predeterminado e intentó usar la sintaxis indexada. Para resolver este error, llame al método de descriptor de acceso `get` o `set` de la propiedad.  
  
## Ejemplo  
  
```  
// CPP1545.cpp // compile with: /clr /LD // a Visual C++ program using namespace System; public ref struct Employee { Employee( String^ s, int d ) {} property String^ name { String^ get() { return nullptr; } } }; public ref struct Manager { property Employee^ Report [String^] { Employee^ get(String^ s) { return nullptr; } void set(String^ s, Employee^ e) {} } };  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1545.  
  
```  
// CS1545.cs // compile with: /r:CPP1545.dll class x { public static void Main() { Manager Ed = new Manager(); Employee Bob = new Employee("Bob Smith", 12); Ed.Report[ Bob.name ] = Bob;   // CS1545 Ed.set_Report( Bob.name, Bob);   // OK } }  
```