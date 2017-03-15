---
title: "Error del compilador CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0171
El campo de copia de seguridad de la propiedad implementada automáticamente 'nombre' se debe asignar por completo antes de devolver el control al llamador. Considere la posibilidad de llamar al constructor predeterminado desde un inicializador de constructor.  
  
 Un constructor en [struct](/dotnet/csharp/language-reference/keywords/struct) debe inicializar todos los campos de la estructura. Para obtener más información, consulta [Constructores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 El ejemplo siguiente genera la advertencia CS0171:  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```