---
title: Varios DSL en una solución
description: Obtenga información sobre cómo puede empaquetar varios lenguajes específicos de dominio (DSL) como parte de una única solución para que se instalen juntos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11baf6439062e28c7361e2fabb4dea4a3430f237
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390924"
---
# <a name="multiple-dsls-in-one-solution"></a>Varios DSL en una solución

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.

Puede usar varias técnicas para integrar varios DSL. Para obtener más información, vea Integración de modelos mediante [Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) y [Cómo:](../modeling/how-to-add-a-drag-and-drop-handler.md) Agregar un controlador de arrastrar y colocar y [Personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Compilación de más de un DSL en la misma solución

1. Cree un nuevo **proyecto de proyecto VSIX.**

2. Cree dos o más proyectos DSL en el directorio de la solución VSIX.

   - Por cada DSL, abra una nueva instancia de Visual Studio. Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.

   - Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.

   - Cambie los nombres de los **proyectos Dsl** y **DslPackage** para que todos sean diferentes. Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - En cada **DslPackage \* \source.extension.tt**, actualice esta línea al nombre de proyecto dsl correcto:

      `string dslProjectName = "Dsl2";`

   - En la solución VSIX, agregue los proyectos Dsl* y \* DslPackage. Quizás quiera coloca cada par en su propia carpeta de solución.

2. Combine los manifiestos VSIX de los DSL:

   1. Abra _YourVsixProject_**\source.extension.manifest**.

   2. Para cada DSL, elija **Agregar contenido** y agregue:

       - `Dsl*` proyecto como componente **mef**

       - `DslPackage*` proyecto como componente **mef**

       - `DslPackage*` proyecto como un **paquete de VS**

3. Compile la solución.

   El VSIX resultante instalará ambos DSL. Puede probarlos mediante F5 o implementar _YourVsixProject_**\bin\Debug \\ \* .vsix**.

## <a name="see-also"></a>Vea también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)