---
title: Cascada de configuración | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
description: Obtenga información sobre la cascada de configuración, la cual organiza la configuración en los niveles de ensamblado, corrección y exploración.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 283cb7b4a485389fa19e3756e79c35f1cec1041a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920505"
---
# <a name="settings-waterfall"></a>Cascada de configuración

El concepto de cascada de configuración significa que el usuario puede especificar opciones en el nivel **Ensamblado**, **Corrección** y **Exploración**:

* Ensamblado: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Corrección: [PexClass](attribute-glossary.md#pexclass)
* Exploración: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Las opciones especificadas en el nivel **Ensamblado** afectan a todas las correcciones y a la exploración en ese ensamblado. Las opciones especificadas en el nivel **Corrección** afectan a todas las exploraciones de esa corrección. Las opciones secundarias tienen preferencia&mdash; si una opción se define en los niveles **Ensamblado** y **Corrección**, se usan las opciones de **Corrección**.

Tenga en cuenta que algunas opciones son específicas del nivel **Ensamblado** o **Corrección**.

**Ejemplo**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=8).
