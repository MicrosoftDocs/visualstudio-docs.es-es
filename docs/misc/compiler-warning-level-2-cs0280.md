---
title: "Advertencia del compilador (nivel 2) CS0280 | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0280
'tipo' no implementa el patrón 'nombre de patrón'. 'nombre de método' tiene una signatura incorrecta.  
  
 Dos instrucciones de C\#, **foreach** y **using**, dependen de los patrones predefinidos "colección" y "recurso", respectivamente. Esta advertencia se produce cuando el compilador no puede hacer coincidir una de estas instrucciones con su patrón debido a la signatura incorrecta de un método. Por ejemplo, el patrón "colección" requiere que haya un método denominado <xref:System.Collections.IEnumerator.MoveNext%2A> que no tome ningún parámetro y devuelva un valor `boolean`. El código podría contener un método <xref:System.Collections.IEnumerator.MoveNext%2A> que tenga un parámetro o quizás devuelva un objeto.  
  
 El patrón "recurso" y `using` proporcionan otro ejemplo. El patrón "recurso" necesita el método <xref:System.IDisposable.Dispose%2A>. Si se define una propiedad con el mismo nombre, aparecerá esta advertencia.  
  
 Para resolver la advertencia, asegúrese de que las signaturas de los métodos del tipo coinciden con las signaturas de los métodos correspondientes del patrón y que no tiene ninguna propiedad con el mismo nombre que un método requerido por el patrón.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0280.  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```