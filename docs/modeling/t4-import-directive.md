---
title: Directiva de importación T4
description: Aprenda que en una plantilla de texto T4 de Visual Studio, la Directiva Import le permite hacer referencia a los elementos de otro espacio de nombres sin proporcionar un nombre completo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dbd42f42213e475452185475a69b1dd9fe5f8e0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363697"
---
# <a name="t4-import-directive"></a>Directiva de importación T4

En los bloques de código de una plantilla de texto T4 de Visual Studio, la `import` directiva le permite hacer referencia a los elementos de otro espacio de nombres sin proporcionar un nombre completo. Es el equivalente de `using` en C# o `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Para obtener información general sobre cómo escribir plantillas de texto T4, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

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

- El espacio de nombres de DSL

## <a name="see-also"></a>Consulta también

- [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)
