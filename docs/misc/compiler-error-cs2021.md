---
title: "Error del compilador CS2021 | Microsoft Docs"
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
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2021
El nombre de archivo 'file' es demasiado largo o no válido  
  
 Ninguno de los nombres de archivo pasados al compilador de C\# debe superar el valor de `_MAX_PATH` \(definido en un archivo de encabezado de Windows\). El compilador generará este error en las situaciones siguientes:  
  
-   Un nombre de archivo \(incluida la ruta de acceso\) tiene una longitud mayor que `_MAX_PATH`.  
  
-   El nombre de archivo contiene caracteres no válidos.  
  
-   El nombre de archivo contiene caracteres comodín, que no están permitidos \(como en los nombres de archivo de recursos\).