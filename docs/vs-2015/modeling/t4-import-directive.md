---
title: T4 Import (directiva) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6fa8f027fbb3418fff47b0459628afb691c8a05a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893681"
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



