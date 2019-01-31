---
title: Acciones rápidas, bombillas y destornilladores
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d1d129e1a7448e814f01c5a60f282fec028ee4a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982226"
---
# <a name="quick-actions"></a>Acciones rápidas

Las acciones rápidas le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción. Las acciones rápidas están disponibles para C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) y los archivos de código de Visual Basic. Algunas acciones son específicos de un lenguaje mientras que otras se aplican a todos los lenguajes.

Las acciones rápidas pueden utilizarse para:

- Aplicar una revisión de código para una infracción de regla del [analizador de código](../code-quality/roslyn-analyzers-overview.md).
- [Suprimir](../code-quality/use-roslyn-analyzers.md) una infracción de regla del analizador de código.
- Aplicar una refactorización (por ejemplo, [insertar una variable temporal](../ide/reference/inline-temporary-variable.md)).
- Generar código (por ejemplo, [introducir una variable local](../ide/reference/introduce-local-variable.md)).

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Refactorización (Visual Studio para Mac)](/visualstudio/mac/refactoring).

Las acciones rápidas se pueden aplicar con los iconos de bombilla ![icono de bombilla](media/light-bulb-icon.png) o de destornillador ![icono de destornillador](media/screwdriver-icon.png) o presionando **Ctrl**+**.** cuando el cursor está en una línea de código para la que está disponible una acción. Verá una bombilla de error ![icono de bombilla de error](media/error-light-bulb-icon.png) si hay un subrayado ondulado de color rojo que indica un error. Visual Studio tiene una corrección disponible para ese error.

Para cualquier lenguaje, un tercero puede proporcionar diagnósticos y sugerencias, por ejemplo, como parte de un SDK, y las bombillas de Visual Studio se encienden siguiendo esas reglas.

## <a name="icons"></a>Iconos

El icono que aparece cuando hay una acción rápida disponible da una indicación del tipo de corrección o refactorización disponible. El icono *destornillador* ![icono de destornillador](media/screwdriver-icon.png) indica que hay acciones disponibles para cambiar el código, pero no es necesario usarlas. El icono *bombilla amarilla* ![icono de bombilla](media/light-bulb-icon.png) indica que hay acciones disponibles que *debe* llevar a cabo para mejorar el código. El icono *bombilla de error* ![icono de bombilla de error](media/error-light-bulb-icon.png) indica que hay una acción disponible que corrige un error del código.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Para ver una bombilla o un destornillador

- Si hay una corrección disponible, aparecerán bombillas espontáneamente cuando mantenga el cursor en la ubicación de un error.

   ![Bombilla con el desplazamiento del mouse](../ide/media/vs2015_lightbulb_hover.png)

- Las bombillas y los destornilladores aparecen en el margen izquierdo del editor cuando mueve el acento circunflejo a una línea de código para la que hay una acción rápida disponible.

- Presione **Ctrl**+**.** en cualquier parte de una línea para ver una lista de acciones rápidas y refactorizaciones disponibles.

## <a name="to-see-potential-fixes"></a>Para ver posibles correcciones

Seleccione la flecha abajo situada junto a la bombilla o el vínculo **Mostrar posibles correcciones** para mostrar una lista de acciones rápidas disponibles.

![Bombilla expandida](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Vea también

- [Generación de código en Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Acciones rápidas comunes](../ide/common-quick-actions.md)
- [Estilos de código y acciones rápidas](../ide/code-styles-and-quick-actions.md)
- [Escribir y refactorizar código (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactorización (Visual Studio para Mac)](/visualstudio/mac/refactoring)