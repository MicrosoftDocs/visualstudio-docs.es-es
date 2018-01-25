---
title: "Acciones rápidas | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 259e033aa32caaca59f37d7dc77ac095b4709878
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="quick-actions"></a>Acciones rápidas

Las acciones rápidas le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción. Las acciones rápidas están disponibles para C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) y los archivos de código de Visual Basic. Algunas acciones son específicos de un lenguaje mientras que otras se aplican a todos los lenguajes.

Las acciones rápidas se pueden aplicar mediante el icono de bombilla ![icono de bombilla pequeño](media/vs2015_lightbulbsmall.png) o presionando **Ctrl**+**.** cuando el cursor esté en la línea de código adecuada. Verá una bombilla si hay una flecha en zigzag de color rojo y Visual Studio tiene una sugerencia para corregir el problema. Por ejemplo, si tiene un error que se indica mediante una flecha en zigzag de color rojo, aparecerá una bombilla cuando haya disponibles correcciones para ese error.

Para cualquier lenguaje, un tercero puede proporcionar diagnósticos y sugerencias, por ejemplo, como parte de un SDK, y las bombillas de Visual Studio se encenderán siguiendo esas reglas.

## <a name="to-see-a-light-bulb"></a>Para ver una bombilla

1. En muchos casos, las bombillas aparecen espontáneamente cuando se desplaza el mouse sobre el punto de error, o en el margen izquierdo del editor cuando se coloca el cursor de inserción en una línea que tiene un error en ella. Cuando vea una flecha zigzagueante de color rojo, puede mover el puntero por encima para mostrar la bombilla. También puede hacer que una bombilla aparezca usando el ratón o el teclado para ir a algún sitio de la línea donde existe el problema.

1. Presione **Ctrl**+**.** en cualquier sitio de una línea para invocar a la bombilla e ir directamente a la lista de posibles correcciones.

   ![Bombilla con el desplazamiento del mouse](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Para ver posibles correcciones

Haga clic en la flecha hacia abajo o en el vínculo Mostrar posibles correcciones para mostrar la lista de acciones rápidas que la bombilla puede llevar a cabo.

![Bombilla expandida](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="see-also"></a>Vea también

[Generación de código en Visual Studio](../ide/code-generation-in-visual-studio.md)  
[Acciones rápidas comunes](../ide/common-quick-actions.md)  
[Estilos de código y acciones rápidas](../ide/code-styles-and-quick-actions.md)  
[Escribir y refactorizar código (C++)](/cpp/ide/writing-and-refactoring-code-cpp)