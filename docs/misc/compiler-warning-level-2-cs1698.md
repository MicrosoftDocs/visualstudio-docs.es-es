---
title: "Advertencia del compilador (nivel 2) CS1698 | Microsoft Docs"
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
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS1698
La referencia de ensamblado circular 'AssemblyName1' no coincide con el nombre del ensamblado de salida 'AssemblyName2'. Pruebe a agregar una referencia a 'AssemblyName1' o a cambiar el nombre del ensamblado de salida para que coincidan.  
  
 La advertencia CS1698 aparece cuando una referencia de ensamblado es incorrecta. Esto puede suceder si se vuelve a compilar un ensamblado de referencia. Para solucionarlo, no reemplace un ensamblado que sea en sí mismo una dependencia de un ensamblado al que se hace referencia.  
  
## Ejemplo  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## Ejemplo  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1698.  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```