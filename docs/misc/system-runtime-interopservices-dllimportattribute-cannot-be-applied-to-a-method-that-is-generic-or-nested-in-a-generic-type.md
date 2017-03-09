---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a un m&#233;todo que es gen&#233;rico o que est&#225; anidado en un tipo gen&#233;rico | Microsoft Docs"
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
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a un m&#233;todo que es gen&#233;rico o que est&#225; anidado en un tipo gen&#233;rico
Se declara un procedimiento con <xref:System.Runtime.InteropServices.DllImportAttribute>, pero el procedimiento es genérico o está contenido en una clase o estructura genérica.  
  
 Common Language Runtime \(CLR\) reconoce este atributo y su propiedad <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> como la designación de un procedimiento de reemplazo definido en una biblioteca de vínculos dinámicos \(DLL\) no administrada fuera de .NET Framework. Si el código llama al procedimiento en el que se aplica <xref:System.Runtime.InteropServices.DllImportAttribute>, Common Language Runtime llama en su lugar al procedimiento no administrado designado.  
  
 Dado que las plataformas no administradas fuera de .NET Framework no reconocen los tipos genéricos, no puede interoperar con ellos usando tipos genéricos.  
  
 **Identificador de error:** BC31526  
  
### Para corregir este error  
  
-   Si ni procedimiento ni su contenedor deben ser genéricos, quite las cláusulas `Of` para que no sean genéricos.  
  
-   Si el procedimiento o su contenedor deben ser genéricos, quite <xref:System.Runtime.InteropServices.DllImportAttribute> de la declaración de este procedimiento.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)