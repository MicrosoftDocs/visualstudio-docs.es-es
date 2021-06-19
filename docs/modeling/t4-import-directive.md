---
title: Directiva de importación T4
description: Obtenga información sobre que, Visual Studio plantilla de texto T4, la directiva import le permite hacer referencia a elementos de otro espacio de nombres sin proporcionar un nombre completo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0d441ec5a62dfa5266a17a06ac8fe33941136c6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386324"
---
# <a name="t4-import-directive"></a>Directiva de importación T4

En los bloques de código de una Visual Studio de texto T4, la directiva permite hacer referencia a elementos de otro espacio de nombres sin proporcionar `import` un nombre completo. Es el equivalente de `using` en C# o `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Para obtener información general sobre cómo escribir plantillas de texto T4, vea [Escribir una plantilla de texto T4.](../modeling/writing-a-t4-text-template.md)

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

- Espacio de nombres del DSL

## <a name="see-also"></a>Vea también

- [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)
