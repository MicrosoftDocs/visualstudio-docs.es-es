---
title: "Advertencia del compilador (nivel 2) CS0728 | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0728
Posiblemente una asignación incorrecta a 'variable' local, que es el argumento a una instrucción using o lock.  La llamada a Dispose o el desbloqueo se producirá en el valor original de la variable local.  
  
 Hay varios escenarios donde `using` o `lock` bloques darán como resultado una pérdida temporal de recursos. Este es un ejemplo:  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 En este caso, el valor original, como null, de la variable `thisType` se desechará cuando el bloque `using` termine la ejecución, pero el objeto `thisType` creado dentro del bloque no estará, aunque eventualmente tendrá los desechos recopilados.  
  
 Para resolver este error, use el formato siguiente:  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 En este caso, el objeto `thisType` recién asignado se eliminará.  
  
## Ejemplo  
 El código siguiente generará la advertencia CS0728.  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```