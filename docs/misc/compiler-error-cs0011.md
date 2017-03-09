---
title: "Error del compilador CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0011
La clase base o la 'clase' de interfaz del ensamblado 'ensamblado' a la que hace referencia el tipo 'tipo' no se ha podido resolver.  
  
 Una clase importada desde un archivo con **\/reference**, se deriva de una clase o implementa una interfaz que no se encuentra. Esto puede ocurrir si un archivo DLL necesario no se incluye también en la compilación con **\/reference**.  
  
 Para obtener más información, vea [Add Reference Dialog Box](http://msdn.microsoft.com/es-es/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) y [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## Ejemplo  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## Ejemplo  
 El segundo archivo crea un archivo DLL que define una clase `C` que se deriva de la clase `B` que se creó en el ejemplo anterior.  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## Ejemplo  
 El tercer archivo reemplaza el archivo DLL creado en el primer paso y omite la definición de la clase interna `B`.  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## Ejemplo  
 Por último, el cuarto archivo hace referencia a la clase `C` definida en el segundo ejemplo, que se deriva de la clase `B`, y que ahora falta.  
  
 El ejemplo siguiente genera la advertencia CS0011:  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## Vea también  
 [Add Reference Dialog Box](http://msdn.microsoft.com/es-es/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)