---
title: "Error del compilador CS0546 | Microsoft Docs"
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
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0546
'accessor': no se puede reemplazar porque 'property' no tiene un descriptor de acceso set reemplazable  
  
 Error al intentar reemplazar uno de los métodos de descriptor de acceso para una propiedad porque no se puede reemplazar el descriptor de acceso. Este error puede producirse en los casos siguientes:  
  
-   Si la propiedad de clase base no está declarada como [virtual](/dotnet/csharp/language-reference/keywords/virtual).  
  
-   Si la propiedad de clase base no declara el descriptor de acceso [get](/dotnet/csharp/language-reference/keywords/get) o [set](/dotnet/csharp/language-reference/keywords/set) que está intentando reemplazar.  
  
 Si no desea reemplazar la propiedad de clase base, puede usar la palabra clave [new](/dotnet/csharp/language-reference/keywords/new) antes de la propiedad en una clase derivada.  
  
 Para obtener más información, consulta [Utilizar propiedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0546 porque la clase base no declara ningún descriptor de acceso set para la propiedad.  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## Vea también  
 [Propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties)