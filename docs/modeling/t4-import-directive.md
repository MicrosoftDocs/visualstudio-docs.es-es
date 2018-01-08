---
title: "T4 Directiva de importación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 5d581e182b39ac5a786b2d66a1a3798ba7fe82ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="t4-import-directive"></a>Directiva de importación T4
En los bloques de código de una plantilla de texto T4 de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la directiva `import` permite hacer referencia a los elementos en otro espacio de nombres sin proporcionar un nombre completo. Es el equivalente de `using` en C# o `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Para obtener una descripción general de la escritura de plantillas de texto T4, vea [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Usar la directiva de importación  
  
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
  
## <a name="standard-imports"></a>Importaciones estándar  
 El siguiente espacio de nombres se importa automáticamente para que no sea necesario escribir una directiva de importación para él:  
  
-   `System`  
  
 Además, si se usa una directiva personalizada, el procesador de directivas podría importar algunos espacios de nombres automáticamente.  
  
 Por ejemplo, si escribe plantillas para un lenguaje específico del dominio (ADSL), no necesita escribir directivas de importación para los siguientes espacios de nombres:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Espacio de nombres del ADSL  
  
## <a name="see-also"></a>Vea también  
 [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)