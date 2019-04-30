---
title: Varios DSL en una solución
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d9e4ae8239994a7524cdd1da0b3cfe05ea42d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808189"
---
# <a name="multiple-dsls-in-one-solution"></a>Varios DSL en una solución

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.

Puede usar varias técnicas para integrar varios DSL. Para obtener más información, consulte [integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) y [Cómo: Agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) y [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Crear más de un DSL en la misma solución

1. Cree un nuevo **proyecto VSIX** proyecto.

2. Cree dos o más proyectos DSL en el directorio de la solución VSIX.

   - Por cada DSL, abra una nueva instancia de Visual Studio. Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.

   - Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.

   - Cambiar los nombres de los **Dsl** y **DslPackage** proyectos para que sean todos diferentes. Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - En cada **DslPackage\*\source.extension.tt**, actualice esta línea con el nombre de proyecto de Dsl correcto:

      `string dslProjectName = "Dsl2";`

   - En la solución VSIX, agregue el Dsl * y DslPackage\* proyectos. Quizás quiera coloca cada par en su propia carpeta de solución.

2. Combine los manifiestos VSIX de los DSL:

   1. Abra _Suproyectovsix_**\source.extension.manifest**.

   2. Para cada DSL, elija **agregar contenido** y agregue:

       - `Dsl*` un proyecto como un **componente MEF**

       - `DslPackage*` un proyecto como un **componente MEF**

       - `DslPackage*` un proyecto como un **VS Package**

3. Compile la solución.

   El VSIX resultante instalará ambos DSL. Puede probarlos mediante F5 o implementar _Suproyectovsix_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>Vea también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)