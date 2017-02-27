---
title: "Valores predeterminados de Visual Basic, Proyectos, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Instrucción Option Explicit, configurar en el IDE"
  - "Instrucción Option Compare, configurar en el IDE"
  - "Instrucción Option Strict, configurar en el IDE"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Valores predeterminados de Visual Basic, Proyectos, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica la configuración predeterminada para las opciones de proyecto de Visual Basic.  Al crear un nuevo proyecto, las instrucciones de opción especificadas se agregan al encabezado del proyecto en el Editor de código.  Las opciones se aplican a todos los proyectos de Visual Basic.  
  
 Para obtener acceso a este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**, expanda la carpeta **Proyectos y soluciones** y, a continuación, haga clic en **Valores predeterminados de VB**.  
  
 **Option Explicit**  
 Establece el valor predeterminado del compilador mediante el cual se obliga a utilizar declaraciones explícitas de las variables.  De forma predeterminada, **Option Explicit** está establecida en **On**.  Para obtener más información, vea [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Establece el valor predeterminado del compilador mediante el cual se obliga a utilizar conversiones de reducción explícitas y se prohíbe el enlace en tiempo de ejecución.  De forma predeterminada, **Option Strict** está establecida en **Off**.  Para obtener más información, vea [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Establece el valor predeterminado del compilador para las comparaciones de cadenas: binario \(distingue entre mayúsculas y minúsculas\) o texto \(sin esta distinción\). De forma predeterminada, **Option Compare** está establecida en **Binary**.  Para obtener más información, vea [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Establece el valor predeterminado del compilador para la inferencia de tipos local.  De manera predeterminada, **Option Infer** está establecida en **On** para los proyectos recién creados y en **Off** para los proyectos migrados creados en versiones anteriores de Visual Basic.  Para obtener más información, vea [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## Vea también  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)