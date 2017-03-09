---
title: "Error del compilador CS0041 | Microsoft Docs"
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
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0041
El nombre completo de 'type' es demasiado largo para la información de depuración. Realice la compilación sin la opción '\/debug'.  
  
 Este error puede producirse al usar la opción [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) del compilador. Si se produce este error, intente eliminar los archivos PDB en el directorio bin y vuelva a realizar la compilación. Si este error persiste, es posible que deba reparar o reinstalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].