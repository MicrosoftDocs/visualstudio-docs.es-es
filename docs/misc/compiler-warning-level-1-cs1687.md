---
title: "Advertencia del compilador (nivel 1) CS1687 | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1687
El archivo de código fuente superó el límite de 16 707 565 líneas representables en el PDB. La información de depuración será incorrecta  
  
 El archivo PDB y el depurador tienen algunas limitaciones sobre el tamaño máximo que puede tener un archivo. Si el archivo de código fuente es demasiado grande, el depurador no se comportará correctamente más allá de ese límite. El usuario no debe emitir información de depuración de ese archivo, quizás usando `#line hidden`, o bien debe encontrar una manera de reducir el archivo, quizás dividiendo el archivo en varios archivos. Puede que el usuario quiera usar la palabra clave `partial` para dividir una clase de gran tamaño.