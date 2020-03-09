---
title: Procedimientos recomendados de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263154"
---
# <a name="msbuild-best-practices"></a>Procedimientos recomendados de MSBuild

Le recomendamos los siguientes procedimientos para escribir scripts de MSBuild:

- Los valores de propiedad predeterminados se controlan mejor mediante el uso del atributo `Condition` sin declarar una propiedad cuyo valor predeterminado se puede reemplazar en la línea de comandos. Por ejemplo, use

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- En general, evite el uso de caracteres comodín al seleccionar elementos. En su lugar, especifique los archivos explícitamente. Esto se debe a que en la mayoría de los tipos de proyecto, MSBuild expande los caracteres comodín en varias ocasiones, como al agregar o quitar elementos, lo que puede provocar un comportamiento inesperado. Una excepción a esto son los proyectos de estilo SDK de .NET Core, que procesan los caracteres comodín correctamente.

## <a name="see-also"></a>Vea también

- [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)
