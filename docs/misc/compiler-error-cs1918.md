---
title: "Error del compilador CS1918 | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1918
Los miembros de la propiedad 'nombre' de tipo 'tipo' no se pueden asignar con un inicializador de objeto porque es de un tipo de valor.  
  
 Este error se produce al intentar usar un inicializador de objeto para inicializar las propiedades de un tipo de estructura que a su vez es una propiedad de la clase que se va a inicializar.  
  
### Para corregir este error  
  
1.  Si debe inicializar completamente los campos de la propiedad en el inicializador de objeto, cambie la estructura a un tipo de clase. De lo contrario, inicialice los miembros de la estructura en una llamada a método independiente después de crear el objeto mediante el inicializador de objeto.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1918:  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)