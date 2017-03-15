---
title: "La palabra clave &#39;&lt;keyword&gt;&#39; se usa para sobrecargar los miembros heredados; no use la palabra clave &#39;&lt;keyword&gt;&#39; cuando sobrecargue un procedimiento &#39;Sub New&#39;. | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La palabra clave &#39;&lt;keyword&gt;&#39; se usa para sobrecargar los miembros heredados; no use la palabra clave &#39;&lt;keyword&gt;&#39; cuando sobrecargue un procedimiento &#39;Sub New&#39;.
Se ha declarado un constructor con la palabra clave `Overloads`.  
  
 Visual Basic no admite la herencia ni la sobrecarga de constructores.  
  
 **Identificador de error:** BC32040  
  
### Para corregir este error  
  
-   Quite la palabra clave `Overloads` de todas las declaraciones de constructor.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)