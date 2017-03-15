---
title: "Error del compilador CS0554 | Microsoft Docs"
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
  - "CS0554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0554"
ms.assetid: 884db4b2-3a69-4434-9a25-526f596e03c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0554
'rutina de conversión': conversión definida por el usuario a clase derivada o desde ella  
  
 No se permiten las conversiones definidas por el usuario a valores de una clase derivada; no es necesario este tipo de operador.  
  
 Consulte el capítulo 6 en la especificación del lenguaje C\# para obtener más información sobre las conversiones definidas por el usuario.  
  
 El ejemplo siguiente genera la advertencia CS0554:  
  
```  
// CS0554.cs namespace x { public class ii { // delete the conversion routine to resolve CS0554 public static implicit operator ii(a aa) // CS0554 { return new ii(); } } public class a : ii { public static void Main() { } } }  
```