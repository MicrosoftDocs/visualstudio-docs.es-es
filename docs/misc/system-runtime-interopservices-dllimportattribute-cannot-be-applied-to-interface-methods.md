---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a m&#233;todos de interfaz. | Microsoft Docs"
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
  - "bc31530"
  - "vbc31530"
helpviewer_keywords: 
  - "BC31530"
ms.assetid: e63f1f7d-b7df-4637-a0f4-2783479ca1af
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a m&#233;todos de interfaz.
Un procedimiento se define dentro de una interfaz, pero la definición de procedimiento se aplica <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 Common Language Runtime \(CLR\) reconoce este atributo y su propiedad <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> como la designación de un procedimiento de reemplazo definido en una biblioteca de vínculos dinámicos \(DLL\) no administrada fuera de .NET Framework. Si el código llama al procedimiento en el que se aplica <xref:System.Runtime.InteropServices.DllImportAttribute>, Common Language Runtime llama en su lugar al procedimiento no administrado designado.  
  
 Dado que la definición de un procedimiento dentro de una interfaz no incluye ninguna implementación, no puede interoperar con plataformas no administradas fuera de .NET Framework.  
  
 **Identificador de error:** BC31530  
  
### Para corregir este error  
  
-   Quite <xref:System.Runtime.InteropServices.DllImportAttribute> de la definición de este procedimiento.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)