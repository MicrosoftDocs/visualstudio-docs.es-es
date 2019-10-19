---
title: Varios DSL en una solución | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668553"
---
# <a name="multiple-dsls-in-one-solution"></a>Varios DSL en una solución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.

 Puede usar varias técnicas para integrar varios DSL. Para obtener más información, vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) y [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) y [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Para compilar más de un DSL en la misma solución

1. Cree dos o más soluciones de DSL y un proyecto de VSIX, y agregue todos los proyectos a una única solución.

   - Para crear un nuevo proyecto de VSIX: en el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#** , **extensibilidad**, **Proyecto VSIX**.

   - Cree dos o más soluciones de DSL en el directorio de soluciones VSIX.

        Por cada DSL, abra una nueva instancia de Visual Studio. Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.

        Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.

   - Cambie los nombres de los proyectos **DSL** y **DslPackage** para que sean distintos. Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - En cada **DslPackage \* \ Source.Extension.TT**, actualice esta línea al nombre del proyecto DSL correcto:

        `string dslProjectName = "Dsl2";`

   - En la solución VSIX, agregue los proyectos DSL * y DslPackage \*.

        Quizás quiera coloca cada par en su propia carpeta de solución.

2. Combine los manifiestos VSIX de los DSL:

   1. Abra _suproyectovsix_ **\source.Extension.manifest**.

   2. Para cada DSL, elija **agregar contenido** y agregar:

       - `Dsl*` proyecto como **componente MEF**

       - `DslPackage*` proyecto como **componente MEF**

       - `DslPackage*` proyecto como **paquete de vs**

3. Compile la solución.

   El VSIX resultante instalará ambos DSL. Puede probarla mediante F5 o implementar _suproyectovsix_ **\bin\debug \\ \*. vsix**.

## <a name="see-also"></a>Vea también
 [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md)
