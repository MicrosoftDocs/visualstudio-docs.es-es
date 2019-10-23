---
title: Cascada de configuración | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: ad5f03d7722fa2fb8452b6a1217c18996d6c978f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653155"
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

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).