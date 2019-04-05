---
title: T4 Import (directiva) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00033640ec7810f97785b38437795906500a7866
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999173"
---
# <a name="t4-import-directive"></a>Directiva de importación T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los bloques de código de una plantilla de texto T4 de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la directiva `import` permite hacer referencia a los elementos en otro espacio de nombres sin proporcionar un nombre completo. Es el equivalente de `using` en C# o `imports` en [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
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
  
- `System`  
  
  Además, si se usa una directiva personalizada, el procesador de directivas podría importar algunos espacios de nombres automáticamente.  
  
  Por ejemplo, si escribe plantillas para un lenguaje específico del dominio (ADSL), no necesita escribir directivas de importación para los siguientes espacios de nombres:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Su espacio de nombres del ADSL  
  
## <a name="see-also"></a>Vea también  
 [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)
