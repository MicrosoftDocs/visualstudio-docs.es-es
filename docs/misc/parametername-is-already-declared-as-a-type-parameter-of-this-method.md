---
title: "&#39;&lt;nombreDePar&#225;metro&gt;&#39; ya se declar&#243; como par&#225;metro de tipo de este m&#233;todo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDePar&#225;metro&gt;&#39; ya se declar&#243; como par&#225;metro de tipo de este m&#233;todo
Un procedimiento genérico define un parámetro normal o una variable local con el mismo nombre como un parámetro de tipo.  
  
 Cada parámetro de un procedimiento, incluso cada parámetro de tipo de un procedimiento genérico, debe tener un nombre distinto de todos los demás parámetros. Puesto que los parámetros de procedimiento se usan como variables locales, cualquier variable local declarada dentro del procedimiento también debe tener un nombre distinto de todos los parámetros y parámetros de tipo.  
  
 **Identificador de error:** BC32089  
  
### Para corregir este error  
  
-   Cambie el nombre del parámetro normal o de la variable local.  
  
## Vea también  
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de parámetros](/dotnet/visual-basic/language-reference/statements/parameter-list)