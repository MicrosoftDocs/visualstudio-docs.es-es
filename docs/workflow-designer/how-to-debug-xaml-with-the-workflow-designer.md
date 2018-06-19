---
title: 'Diseñador de flujo de trabajo: Cómo: depurar código XAML con el Diseñador de flujo de trabajo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eac6294861080614cbdd46e6ac1cc9a05d7124ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969901"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Depurar XAML con el Diseñador de flujo de trabajo

Los flujos de trabajo se definen en términos de código XAML. La representación de la interfaz de usuario de flujo de trabajo se compila sobre el árbol XAML que define el flujo de trabajo. La experiencia de depuración es similar a depurar flujos de trabajo en el Diseñador de flujo de trabajo de Windows. Por ejemplo, durante la depuración de XAML, las variables locales, inspección y ventanas subprocesos funcionan del mismo modo que en el Diseñador de flujo de trabajo de depuración. Además, la vista de pila de llamadas durante la depuración de código XAML es una vista jerárquica basada en líneas del flujo de ejecución para el flujo de trabajo.

> [!NOTE]
> Si el XAML para un flujo de trabajo se encuentra en el mismo ensamblado que las actividades, la parte del ensamblado de los nombres de clase no se incluye. Sin esta parte de los nombres de clase (actividad), el XAML no se puede cargar en tiempo de ejecución. No se recomienda definir actividades en el mismo espacio de nombres que el proyecto principal; si no, el XAML necesitará editarse a mano después de editarse en el diseñador.

## <a name="to-debug-workflow-xaml"></a>Para depurar el XAML de flujo de trabajo

1.  En Visual Studio, abra un proyecto de flujo de trabajo o actividad.

2.  Establecer un punto de interrupción en la actividad o actividades que desea depurar tal y como se describe en [Cómo: establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Haga clic en el archivo .xaml que contiene la definición de flujo de trabajo y seleccione **ver código**. Verá un punto de interrupción que se muestra en la misma línea que la declaración del elemento XAML de la actividad para la que establece el punto de interrupción en la vista de diseño.

4.  Invocar el depurador, como se describe en [Cómo: invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Cuando la ejecución del código llegue a uno de los puntos de interrupción, se resaltará el elemento XAML asociado a ese punto de interrupción. Para mover el siguiente punto de interrupción, use la **F10** o **F11** clave.

## <a name="see-also"></a>Vea también

- [Cómo: Establecer puntos de interrupción en los flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Cómo: Invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md)