---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a un m&#233;todo de instancia | Microsoft Docs"
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
  - "vbc31529"
  - "bc31529"
helpviewer_keywords: 
  - "BC31529"
ms.assetid: c8bde5d7-c6bf-4d21-bb1a-e8627d65ad29
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a un m&#233;todo de instancia
Se declara un procedimiento no compartido con <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 Common Language Runtime \(CLR\) reconoce este atributo y su propiedad <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> como la designación de un procedimiento de reemplazo definido en una biblioteca de vínculos dinámicos \(DLL\) no administrada fuera de .NET Framework. Si el código llama al procedimiento en el que se aplica <xref:System.Runtime.InteropServices.DllImportAttribute>, Common Language Runtime llama en su lugar al procedimiento no administrado designado.  
  
 Como las plataformas no administradas fuera de .NET Framework no admiten procedimientos no compartidos de la misma manera que .NET Framework, no puede interoperar con ellas mediante procedimientos no compartidos.  
  
 **Id. de error:** BC31529  
  
### Para corregir este error  
  
-   Si no es necesario que el procedimiento se aplique individualmente a cada instancia de su clase o estructura, declárelo como `Shared`.  
  
-   Si el procedimiento no puede ser `Shared`, quite <xref:System.Runtime.InteropServices.DllImportAttribute> de la declaración de este procedimiento.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)