---
title: "Advertencia del compilador (nivel 1) CS3016 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3016"
ms.assetid: b2ae721d-13ab-4e9d-a288-741d7825defe
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3016
El uso de matrices como argumentos de atributo no es conforme a CLS  
  
 No es conforme con Common Language Specification \(CLS\) pasar una matriz a un atributo. Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3016:  
  
```  
// CS3016.cs using System; [assembly : CLSCompliant(true)] [C(new int[] {1, 2})]   // CS3016 // try the following line instead // [C()] class C : Attribute { public C() { } public C(int[] a) { } public static void Main () { } }  
```