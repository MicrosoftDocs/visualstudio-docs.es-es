---
title: 'Diseñador de flujo de trabajo: depurar XAML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9be7c8da251a9698e0fceba64e3941ba8fbdf803
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817520"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Depurar XAML con el Diseñador de flujo de trabajo

Los flujos de trabajo se definen en términos de código XAML. La representación de la interfaz de usuario de flujo de trabajo se compila sobre el árbol XAML que define el flujo de trabajo. La experiencia de depuración es similar a la depuración de flujos de trabajo en el Diseñador de flujo de trabajo. Por ejemplo, al depurar XAML, las ventanas variables locales, inspección y subprocesos funcionan de la misma manera que en Diseñador de flujo de trabajo depuración. Además, la vista de pila de llamadas durante la depuración de código XAML es una vista jerárquica basada en líneas del flujo de ejecución para el flujo de trabajo.

> [!NOTE]
> Si el XAML para un flujo de trabajo se encuentra en el mismo ensamblado que las actividades, la parte del ensamblado de los nombres de clase no se incluye. Sin esta parte de los nombres de clase (actividad), el XAML no se puede cargar en tiempo de ejecución. No se recomienda definir actividades en el mismo espacio de nombres que el proyecto principal; si no, el XAML necesitará editarse a mano después de editarse en el diseñador.

## <a name="to-debug-workflow-xaml"></a>Para depurar el XAML de flujo de trabajo

1. Abra un proyecto de flujo de trabajo o actividad en Visual Studio.

2. Establezca un punto de interrupción en la actividad o actividades que desee depurar, tal y como se describe en [Cómo: establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Haga clic con el botón secundario en el archivo. XAML que contiene la definición de flujo de trabajo y seleccione **Ver código**. Verá un punto de interrupción que se muestra en la misma línea que la declaración del elemento XAML de la actividad para la que establece el punto de interrupción en la vista de diseño.

4. Invoque el depurador tal como se describe en [Depurar flujos de trabajo](debugging-workflows-with-the-workflow-designer.md).

5. Cuando la ejecución del código llegue a uno de los puntos de interrupción, se resaltará el elemento XAML asociado a ese punto de interrupción. Para ir al siguiente punto de interrupción, use la tecla **F10** o **F11** .

## <a name="see-also"></a>Consulte también

- [Cómo: Establecer puntos de interrupción en los flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Flujos de trabajo de depuración](debugging-workflows-with-the-workflow-designer.md)
