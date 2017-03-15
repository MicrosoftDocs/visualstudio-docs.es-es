---
title: "Los argumentos de tipo inferidos para el m&#233;todo &#39;&lt;procedurename&gt;&#39; generan las siguientes advertencias: &lt;warninglist&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los argumentos de tipo inferidos para el m&#233;todo &#39;&lt;procedurename&gt;&#39; generan las siguientes advertencias: &lt;warninglist&gt;
Se llama a un procedimiento genérico sin facilitar argumentos de tipo y los argumentos de tipo deducidos generan en una o varias advertencias.  
  
 Normalmente, cuando se invoca un tipo genérico, se facilita un argumento de tipo para cada parámetro de tipo que define el tipo genérico. Si no facilita ningún argumento de tipo, el compilador intenta deducir los tipos que se pasan a los parámetros de tipo. Si existe ambigüedad en los tipos deducidos o crean una situación que podría provocar resultados inesperados, el compilador genera esta advertencia.  
  
 Una *restricción* en un parámetro de tipo limita los argumentos de tipo que se le pueden pasar. Por ejemplo, un parámetro de tipo puede restringirse para que sea una clase que implemente la interfaz <xref:System.IComparable%601>. Para más información, vea "Restricciones" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC41006  
  
### Para corregir este error  
  
-   Facilite argumentos de tipo al procedimiento genérico para que el compilador no tenga que deducirlos.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)