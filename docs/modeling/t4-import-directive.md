---
title: Directiva de importación T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49ab8d3462877a28cf40aed519b71615b23f8d4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914076"
---
# <a name="t4-import-directive"></a>Directiva de importación T4

En los bloques de código de una plantilla de texto T4 de Visual Studio, el `import` directiva le permite hacer referencia a los elementos de otro espacio de nombres sin proporcionar un nombre completo. Es el equivalente de `using` en C# o `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

- Espacio de nombres de su DSL

## <a name="see-also"></a>Vea también

- [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)