---
title: Varios DSL en una solución
description: Obtenga información sobre cómo puede empaquetar varios lenguajes específicos de dominio (DSL) como parte de una única solución para que se instalen juntos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10eeee4d36e6a28bb6cd872573c500bbdf6dca14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950351"
---
# <a name="multiple-dsls-in-one-solution"></a>Varios DSL en una solución

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.

Puede usar varias técnicas para integrar varios DSL. Para obtener más información, vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) y [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) y [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Crear más de un DSL en la misma solución

1. Cree un nuevo proyecto de **Proyecto VSIX** .

2. Cree dos o más proyectos DSL en el directorio de la solución VSIX.

   - Por cada DSL, abra una nueva instancia de Visual Studio. Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.

   - Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.

   - Cambie los nombres de los proyectos **DSL** y **DslPackage** para que sean distintos. Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - En cada **DslPackage \* \ Source.Extension.TT**, actualice esta línea al nombre del proyecto DSL correcto:

      `string dslProjectName = "Dsl2";`

   - En la solución VSIX, agregue los proyectos DSL * y DslPackage \* . Quizás quiera coloca cada par en su propia carpeta de solución.

2. Combine los manifiestos VSIX de los DSL:

   1. Abra _suproyectovsix_**\source.Extension.manifest**.

   2. Para cada DSL, elija **agregar contenido** y agregar:

       - `Dsl*` proyecto como **componente MEF**

       - `DslPackage*` proyecto como **componente MEF**

       - `DslPackage*` proyecto como **paquete de vs**

3. Compile la solución.

   El VSIX resultante instalará ambos DSL. Puede probarla mediante F5 o implementar _suproyectovsix_**\bin\debug \\ \* . vsix**.

## <a name="see-also"></a>Vea también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)