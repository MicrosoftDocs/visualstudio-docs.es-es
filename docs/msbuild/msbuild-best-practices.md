---
title: Procedimientos recomendados de MSBuild | Microsoft Docs
description: Obtenga información sobre los procedimientos recomendados para escribir scripts de MSBuild, como el uso de atributos Condition y el no uso de caracteres comodín.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047662"
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
