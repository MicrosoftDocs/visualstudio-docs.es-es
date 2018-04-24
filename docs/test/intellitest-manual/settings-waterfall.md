---
title: Cascada de configuración | Herramientas de prueba para desarrolladores de Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9265fd0ada4f966f5d5fba01591e10f5f0a4194f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="settings-waterfall"></a>Cascada de configuración

El concepto de cascada de configuración significa que el usuario puede especificar opciones en el nivel **Ensamblado**, **Corrección** y **Exploración**: 

* Ensamblado: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Corrección: [PexClass](attribute-glossary.md#pexclass)
* Exploración: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Las opciones especificadas en el nivel **Ensamblado** afectarán a todas las correcciones y a la exploración en ese ensamblado. Las opciones especificadas en el nivel **Corrección** afectarán a todas las exploraciones de esa corrección. Las opciones secundarias tienen preferencia: si una opción se define en los niveles **Ensamblado** y **Corrección**, se usarán las opciones de **Corrección**.

Tenga en cuenta que algunas opciones son específicas del nivel **Ensamblado** o **Corrección**. 

**Ejemplo**

```
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

Publique sus ideas y solicitudes de características en **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
