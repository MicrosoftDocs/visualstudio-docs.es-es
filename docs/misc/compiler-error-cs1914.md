---
title: "Error del compilador CS1914 | Microsoft Docs"
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
  - "CS1914"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1914"
ms.assetid: e61361b6-4660-41fd-a574-cc48e1b3873c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1914
No se puede asignar el campo estático 'nombre' en un inicializador de objeto  
  
 Los inicializadores de objetos por definición inicializan objetos o instancias de clases. No se pueden usar para inicializar un campo `static` de un tipo. Independientemente del número de instancias de una clase que se creen, solo hay una copia de un campo `static`.  
  
### Para corregir este error  
  
1.  Cambie el campo a un campo de instancia en el tipo, o elimine el intento de inicializarlo desde el inicializador de objeto.  
  
## Ejemplo  
 El código siguiente genera CS1914 porque el inicializador intenta inicializar el campo `TestClass.Number`, que es `static`:  
  
```  
// cs1914.cs using System.Linq; public class TestClass { public string Message { get; set; } public static int Number { get; set; } } class Test { static void Main() { TestClass b = new TestClass() { Message = "Hello", Number = "555-1212" }; // CS1914 } }  
```