---
title: Acciones rápidas
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 43198f5722de1bd983991df8ff19b17fcaea9e83
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="quick-actions"></a>Acciones rápidas

Las acciones rápidas le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción. Las acciones rápidas están disponibles para C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) y los archivos de código de Visual Basic. Algunas acciones son específicos de un lenguaje mientras que otras se aplican a todos los lenguajes.

Las acciones rápidas pueden utilizarse para:

- Aplicar una revisión de código para una infracción de regla del [analizador de código](../code-quality/roslyn-analyzers-overview.md).
- [Suprimir](../code-quality/use-roslyn-analyzers.md) una infracción de regla del analizador de código.
- Aplicar una refactorización (por ejemplo, [insertar una variable temporal](../ide/reference/inline-temporary-variable.md)).
- Generar código (por ejemplo, [introducir una variable local](../ide/reference/introduce-local-variable.md)).

Las acciones rápidas se pueden aplicar mediante el icono de bombilla ![icono de bombilla pequeño](media/vs2015_lightbulbsmall.png) o presionando **Ctrl**+**.** cuando el cursor está en una línea de código para la que está disponible una acción. Verá una bombilla si hay una flecha en zigzag de color rojo y Visual Studio tiene una sugerencia para corregir el problema. Por ejemplo, si tiene un error que se indica mediante una flecha en zigzag de color rojo, aparecerá una bombilla cuando haya disponibles correcciones para ese error.

Para cualquier lenguaje, un tercero puede proporcionar diagnósticos y sugerencias, por ejemplo, como parte de un SDK, y las bombillas de Visual Studio se encienden siguiendo esas reglas.

## <a name="to-see-a-light-bulb"></a>Para ver una bombilla

1. En muchos casos, las bombillas aparecen espontáneamente cuando se desplaza el mouse sobre el punto de error, o en el margen izquierdo del editor cuando se coloca el cursor de inserción en una línea que contiene un error. Cuando vea una flecha zigzagueante de color rojo, puede mover el puntero por encima para mostrar la bombilla. También puede hacer que una bombilla aparezca usando el ratón o el teclado para ir a algún sitio de la línea donde existe el problema.

1. Presione **Ctrl**+**.** en cualquier sitio de una línea para invocar a la bombilla e ir directamente a la lista de posibles correcciones.

   ![Bombilla con el desplazamiento del mouse](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>Para ver posibles correcciones

Haga clic en la flecha abajo o en el vínculo **Mostrar posibles correcciones** para mostrar una lista de acciones rápidas que la bombilla puede llevar a cabo.

![Bombilla expandida](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Vea también

- [Generación de código en Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Acciones rápidas comunes](../ide/common-quick-actions.md)
- [Estilos de código y acciones rápidas](../ide/code-styles-and-quick-actions.md)
- [Escribir y refactorizar código (C++)](/cpp/ide/writing-and-refactoring-code-cpp)