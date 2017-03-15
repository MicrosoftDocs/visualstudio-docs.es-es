---
title: "Use la opci&#243;n &#39;&lt;opci&#243;n&gt;&#39; de la l&#237;nea de comandos o la configuraci&#243;n de proyecto adecuada en vez de &#39;&lt;par&#225;metro&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Use la opci&#243;n &#39;&lt;opci&#243;n&gt;&#39; de la l&#237;nea de comandos o la configuraci&#243;n de proyecto adecuada en vez de &#39;&lt;par&#225;metro&gt;&#39;
La mejor manera de especificar un archivo que contenga una clave pública para un ensamblado, un contenedor de clave pública para un ensamblado o un ensamblado con firma parcial es usar las opciones del compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. No se recomienda usar los atributos <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> o <xref:System.Reflection.AssemblyDelaySignAttribute> en el código.  
  
 **Identificador de error:** BC41008  
  
### Para corregir este error  
  
1.  Use las opciones del compilador [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile), [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) o [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en lugar de los atributos <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> o <xref:System.Reflection.AssemblyDelaySignAttribute> en el código.  
  
## Vea también  
 [Cómo: Crear ensamblados de confianza firmados](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)