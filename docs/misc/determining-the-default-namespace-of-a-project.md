---
title: "Determinaci&#243;n del espacio de nombres predeterminado de un proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas personalizadas, cálculo del espacio de nombres predeterminado"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Determinaci&#243;n del espacio de nombres predeterminado de un proyecto
Por [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], si la propiedad de `CustomToolNamespace` se establece en el archivo de entrada, el valor de `CustomToolNamespace` se convierte el valor del parámetro de espacio de nombres predeterminado pasada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .  Si no, el parámetro de `wszDefaultNamespace` pasado a `Generate` siempre es igual al espacio de nombres.  Para obtener más información sobre los espacios de nombres, vea [Palabras clave del espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace-keywords).  
  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] utiliza espacios de nombres basados en carpetas.  Es decir, el espacio de nombres consta del espacio de nombres, varios nombres de cualquier carpeta que contiene la herramienta personalizada.  Cada nombre de la carpeta se convierte en un identificador válido, y puntos dividen todos los nombres.  Por ejemplo, si el archivo de entrada es FolderA \\FolderB\\FolderC\\MyInput.txt, and the root namespace is CL 9, el espacio de nombres predeterminado calculado es **CL9.FolderA.FolderB.FolderC**.  
  
 Una excepción a esta regla se produce cuando la cadena de la jerarquía contiene una carpeta de referencia web.  Por ejemplo, si:  
  
-   FolderC era una carpeta de referencia web, el espacio de nombres sería **CL9.FolderC**.  
  
-   FolderB era una carpeta de referencia web, el espacio de nombres sería **CL9.FolderB.FolderC**.  
  
 es decir, el espacio de nombres utiliza el formato siguiente:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## Vea también  
 [Implementar generadores de un solo archivo](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrar generadores de un solo archivo](../extensibility/internals/registering-single-file-generators.md)   
 [Exponer tipos de diseñadores visuales](../extensibility/internals/exposing-types-to-visual-designers.md)