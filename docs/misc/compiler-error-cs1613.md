---
title: "Error del compilador CS1613 | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1613
No se encuentra la clase contenedora de coclases administrada de la interfaz 'interface' \(¿falta alguna referencia de ensamblado?\)  
  
 Se intentó crear una instancia de un objeto COM de una interfaz. La interfaz tiene los atributos **ComImport** y `CoClass`, pero el compilador no puede encontrar el tipo dado para el atributo `CoClass`.  
  
 Para solucionar este error, pruebe una de las propuestas siguientes:  
  
-   Agregue una referencia al ensamblado que tenga la coclase \(la mayoría de las veces, la interfaz y la coclase deben estar en el mismo ensamblado\). Vea [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) o [Agregar cuadro de diálogo de referencia](http://msdn.microsoft.com/es-es/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) para obtener información.  
  
-   Corrija el atributo `CoClass` en la interfaz.  
  
 El siguiente ejemplo muestra el uso correcto de **CoClassAttribute**:  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```