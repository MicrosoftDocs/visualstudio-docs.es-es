---
title: "Error del compilador CS0021 | Microsoft Docs"
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
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0021
No se puede aplicar la indexación con \[\] a una expresión de tipo 'tipo'  
  
 Se intentó acceder a un valor a través de un indexador en un tipo de datos que no admite [Indizadores](/dotnet/csharp/programming-guide/indexers/index).  
  
 Es posible que se muestre el error CS0021 si intenta usar un indexador en un ensamblado de C\+\+. En este caso, decore la clase de C\+\+ con el atributo `DefaultMember` para que el compilador de C\# sepa qué indexador es el predeterminado. El ejemplo siguiente genera la advertencia CS0021.  
  
## Ejemplo  
 Este archivo se compila en un archivo .dll, con el atributo `DefaultMember` convertido en comentario, para generar el error.  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## Ejemplo  
 El siguiente es el archivo de C\# que llama al archivo .dll. Este archivo intenta acceder a la clase a través de un indexador, pero dado que no se declaró ningún miembro como el indexador predeterminado que se utilizará, se genera el error.  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```