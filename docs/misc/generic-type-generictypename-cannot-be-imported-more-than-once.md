---
title: "El tipo gen&#233;rico &#39;&lt;generictypename&gt;&#39; no se puede importar m&#225;s de una vez | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo gen&#233;rico &#39;&lt;generictypename&gt;&#39; no se puede importar m&#225;s de una vez
Un [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) especifica un tipo genérico que ya se ha importado con una parametrización de tipo diferente.  
  
 Puede declarar varios tipos construidos a partir de un tipo genérico porque no se define el tipo genérico mediante la declaración de un tipo construido. Sin embargo, si importa un tipo genérico más de una vez, este será el equivalente de varias definiciones.  
  
 **Identificador de error:** BC32086  
  
### Para corregir este error  
  
1.  Si el archivo de origen que contiene esta instrucción `Imports` también contiene otra instrucción `Imports` que especifica el mismo tipo genérico, quite una de ellas.  
  
2.  Si necesita importar el mismo tipo genérico con distintas parametrizaciones de tipo, use varios archivos de origen.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)