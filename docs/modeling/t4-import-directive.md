---
title: "T4 Import Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 Import Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En los bloques de código de una plantilla de texto T4 de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la directiva `import` permite hacer referencia a los elementos en otro espacio de nombres sin proporcionar un nombre completo.  Es el equivalente de `using` en C\# o `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Para obtener información general sobre cómo escribir plantillas de texto T4, vea [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Usar la directiva de importación  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 En este ejemplo, el código de plantilla puede omitir un espacio de nombres explícito para los miembros de System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## Importaciones estándar  
 El siguiente espacio de nombres se importa automáticamente para que no sea necesario escribir una directiva de importación para él:  
  
-   `System`  
  
 Además, si se usa una directiva personalizada, el procesador de directivas podría importar algunos espacios de nombres automáticamente.  
  
 Por ejemplo, si escribe plantillas para un lenguaje específico del dominio \(ADSL\), no necesita escribir directivas de importación para los siguientes espacios de nombres:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Su espacio de nombres del ADSL  
  
## Vea también  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)