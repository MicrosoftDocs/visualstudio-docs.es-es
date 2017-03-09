---
title: "Advertencia del compilador (nivel 1) CS3027 | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3027
'type\_1' no es conforme con CLS porque la interfaz base 'type\_2' no es conforme con CLS  
  
 Un tipo que no es conforme con CLS no puede ser un tipo base de un tipo que es conforme con CLS.  
  
## Ejemplo  
 El ejemplo siguiente contiene una interfaz con un método que utiliza un tipo no conforme con CLS en su firma, lo que hace que el tipo no sea conforme con CLS.  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS3027.  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```