---
title: "Error del compilador CS0082 | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0082
El tipo 'type' reserva ya un miembro denominado 'name' con los mismos tipos de parámetro.  
  
 Las propiedades en tiempo de compilación se convierten en métodos con `get_` o `set_` delante del identificador. Si define su propio método y entra en conflicto con el nombre del método, se genera un error.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0082:  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties)