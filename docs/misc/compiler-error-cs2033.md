---
title: "Error del compilador CS2033 | Microsoft Docs"
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
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2033
No se puede crear un nombre de archivo corto 'filename' cuando ya existe un nombre de archivo largo con el mismo nombre de archivo corto  
  
 Compile cualquier archivo C\# con un nombre de más de ocho caracteres. A continuación, compile otro archivo con la versión abreviada del nombre de archivo anterior, como los seis primeros caracteres del nombre más "~1". En la segunda compilación se generará este error.  
  
 Para resolver este error, cambie el nombre de archivo corto por uno que no entre en conflicto con el nombre de archivo largo.