---
title: "El tipo &#39;&lt;nombreTipo&gt;&#39; debe ser un tipo de valor o un argumento de tipo restringido a &#39;Structure&#39; para poder usarlo con &#39;Nullable&#39; o el modificador &#39;?&#39; que acepta valores NULL. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33101"
  - "bc33101"
helpviewer_keywords: 
  - "BC33101"
ms.assetid: b3e0e4e4-87b8-4a38-a450-15233497acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreTipo&gt;&#39; debe ser un tipo de valor o un argumento de tipo restringido a &#39;Structure&#39; para poder usarlo con &#39;Nullable&#39; o el modificador &#39;?&#39; que acepta valores NULL.
Solo se puede declarar que aceptan valores NULL los tipos de valor, incluidas las estructuras.  
  
```vb#  
' Valid. Dim n? As Integer Dim m As Integer? ' Not valid. ' Dim p? As Object ' Dim q As Nullable(Of Object)  
```  
  
 **Identificador de error:** BC33101  
  
### Para corregir este error  
  
-   Quite '?' o `Nullable`.  
  
-   Use un tipo de datos.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)