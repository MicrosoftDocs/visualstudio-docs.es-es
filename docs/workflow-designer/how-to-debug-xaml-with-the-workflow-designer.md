---
title: 'Diseñador de flujo de trabajo - Cómo: Depurar XAML con el Diseñador de flujo de trabajo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4caf96c841b794a76a7aba35f9c8ca302de6e885
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923335"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Filtrar Depurar XAML con el Diseñador de flujo de trabajo

Los flujos de trabajo se definen en términos de código XAML. La representación de la interfaz de usuario de flujo de trabajo se compila sobre el árbol XAML que define el flujo de trabajo. La experiencia de depuración es similar a la depuración de flujos de trabajo en el Diseñador de flujo de trabajo. Por ejemplo, durante la depuración de XAML, las variables locales, inspección y ventanas de subprocesos funcionan del mismo modo que lo hacen en el Diseñador de flujo de trabajo de depuración. Además, la vista de pila de llamadas durante la depuración de código XAML es una vista jerárquica basada en líneas del flujo de ejecución para el flujo de trabajo.

> [!NOTE]
> Si el XAML para un flujo de trabajo se encuentra en el mismo ensamblado que las actividades, la parte del ensamblado de los nombres de clase no se incluye. Sin esta parte de los nombres de clase (actividad), el XAML no se puede cargar en tiempo de ejecución. No se recomienda definir actividades en el mismo espacio de nombres que el proyecto principal; si no, el XAML necesitará editarse a mano después de editarse en el diseñador.

## <a name="to-debug-workflow-xaml"></a>Para depurar el XAML de flujo de trabajo

1.  En Visual Studio, abra un proyecto de flujo de trabajo o actividad.

2.  Establecer un punto de interrupción en la actividad o actividades que desea depurar tal como se describe en [Cómo: Establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Haga clic en el archivo .xaml que contiene la definición de flujo de trabajo y seleccione **ver código**. Verá un punto de interrupción que se muestra en la misma línea que la declaración del elemento XAML de la actividad para la que establece el punto de interrupción en la vista de diseño.

4.  Invocar el depurador, como se describe en [depurar flujos de trabajo](debugging-workflows-with-the-workflow-designer.md).

5.  Cuando la ejecución del código llegue a uno de los puntos de interrupción, se resaltará el elemento XAML asociado a ese punto de interrupción. Para mover el siguiente punto de interrupción, use la **F10** o **F11** clave.

## <a name="see-also"></a>Vea también

- [Cómo: Establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Depurar flujos de trabajo](debugging-workflows-with-the-workflow-designer.md)