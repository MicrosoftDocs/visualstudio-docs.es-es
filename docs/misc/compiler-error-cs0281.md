---
title: "Error del compilador CS0281 | Microsoft Docs"
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
  - "CS0281"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0281"
ms.assetid: 3b886510-6e4d-45bc-b885-3ab7f6b6b2c6
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0281
Se ha concedido acceso de confianza a 'AssemblyName1', pero el ensamblado de salida se denomina 'AssemblyName2'. Pruebe a agregar una referencia a 'AssemblyName1' o a cambiar el nombre de ensamblado de salida para que coincida.  
  
 El acceso de confianza es una nueva característica de Common Language Runtime \(CLR\) que permite a un ensamblado ver los tipos no públicos de otro ensamblado. Este error se produce cuando el ensamblado que concede acceso de confianza especifica un nombre incorrecto para el ensamblado del que recibe la concesión. Para obtener más información, consulta [Ensamblados de confianza](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Ejemplo  
 La siguiente secuencia de ejemplos de código generará el error CS0281.  
  
 Los archivos utilizados para crear los ensamblados con nombre seguro se generan como sigue:  
  
-   sn \-d CS0281.snk  
  
-   sn \-k CS0281.snk  
  
-   sn \-i CS0281.snk CS0281.snk  
  
-   sn \-pc CS0281.snk key.publickey  
  
-   sn \-tp key.publickey  
  
```  
// CS0281.cs // compile with: /target:library /keyfile:CS0281.snk public class A {}  
```  
  
## Ejemplo  
  
```  
// CS0281_b.cs // compile with: /target:library /keyfile:CS0281.snk /reference:CS0281.dll [assembly:System.Runtime.CompilerServices.InternalsVisibleTo("CS0281 , PublicKey=00240000048000009400000006020000002400005253413100040000010001004b2d4d56af7c50be2fcbbf97cb880b9e73ad84467a587191fef63aadc118a96cecf9d508cd679c907b6e20f71684300bdc2c0a851019af0c96b29bf8f1339753276041aefd67db46139e6348b3a12f29537b4dc6c2c19829df2c9ed6803f3c63c3b84cfa2728849386aea575c543a5f70fa85793d2946f15f7fe1ccb0c5e8fe0")] class B : A {}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0281.  
  
 Observe que este ejemplo crea un archivo de salida con el mismo nombre que el archivo de salida en el primer ejemplo. Para resolver, no cambie los atributos de ensamblado del componente y agregue la clase C.  
  
```  
// CS0281_c.cs // compile with: /target:library /out:CS0281.dll /keyfile:CS0281.snk /reference:CS0281_b.dll // CS0281 expected [assembly:System.Reflection.AssemblyVersion("3")] [assembly:System.Reflection.AssemblyCulture("en-us")] class C : B {} public class A {}  
```