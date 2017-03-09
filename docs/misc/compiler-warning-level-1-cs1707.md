---
title: "Advertencia del compilador (nivel 1) CS1707 | Microsoft Docs"
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
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1707
El delegado 'NombreDelegado' se ha enlazado a 'nombreMétodo1' en lugar de a 'nombreMétodo2' a causa de nuevas reglas de lenguaje.  
  
 C\# 2.0 implementa nuevas reglas para enlazar un delegado a un método. Se considera que la información adicional no se ha consultado en el pasado. Esta advertencia indica que el delegado está enlazado ahora a una sobrecarga diferente del método a la que estaba enlazado anteriormente. Puede que quiera comprobar que el delegado debe enlazarse realmente a 'nombreMétodo1' en lugar de a 'nombreMétodo2'.  
  
 Para obtener una descripción de cómo el compilador determina a qué método debe enlazar un delegado, vea [Usar varianza en delegados](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).