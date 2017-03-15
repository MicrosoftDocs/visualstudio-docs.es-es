---
title: "Error del compilador CS0313 | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0313
El tipo 'type1' no se puede usar como parámetro de tipo 'parameter name' en el tipo o método genéricos 'type2'. El tipo que acepta valores NULL 'type1' no cumple la restricción de 'type2'. Los tipos que aceptan valores NULL no cumplen las restricciones de interfaz.  
  
 Un tipo que acepte valores NULL no es equivalente a su homólogo que no acepte valores NULL. En el ejemplo siguiente, `ImplStruct` cumple la restricción `BaseInterface`, pero `ImplStruct?` no la cumple porque `Nullable<ImplStruct>` no implementa `BaseInterface`.  
  
### Para corregir este error  
  
1.  Con el código siguiente como ejemplo, una solución consiste en especificar un elemento `ImplStruct` normal como el primer argumento de tipo en la llamada a `TestMethod`. Después, modifique `TestMethod` para crear una versión que acepta valores NULL de `Implstruct` en su instrucción return:  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## Ejemplo  
 El código siguiente genera el error CS0313:  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## Vea también  
 [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index)