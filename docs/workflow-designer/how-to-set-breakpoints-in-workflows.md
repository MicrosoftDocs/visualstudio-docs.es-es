---
title: 'Diseñador de flujo de trabajo - Cómo: establecer puntos de interrupción en flujos de trabajo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1d7dcb437a77bd91c8dbb3360a33c7260fabb91
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755244"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Cómo: establecer puntos de interrupción en flujos de trabajo

Cuando se usa el Diseñador de flujo de trabajo, puede establecer puntos de interrupción en los flujos de trabajo gráficas como lo haría en el código de Visual Basic o C#. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.

Un punto de interrupción tiene tres estados: *pendiente*, *enlazados*, y *Error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo. Cuando el tiempo de ejecución haya cargado el tipo de flujo de trabajo, pasa a Enlazado. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.

> [!NOTE]
> No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.

> [!NOTE]
> Asegúrese de seleccionar la opción **habilitar solo mi código (solo administrado)** desde el **herramientas** > **opciones** > **depuración**  menú antes de depurar. Si no está seleccionada la opción tiene dos secuencias anidadas en otra secuencia y establezca un punto de interrupción en la primera secuencia interna, al presionar **F11** no se depurará la segunda secuencia interna.

> [!NOTE]
> No se alcancen los puntos de interrupción en un flujo de trabajo si la ruta de acceso completa a la propiedad del archivo XAML no es preciso. La ruta de acceso completa al archivo XAML no es preciso después de mover el proyecto o solución a otra carpeta o a otra máquina. Seleccione **Ctrl**+**S** para guardar y actualizar la propiedad de ruta de acceso completa.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para establecer un punto de interrupción en una actividad en la vista Diseño

1. Seleccione la actividad donde desee que se interrumpa el depurador.

2. En el **depurar** menú, seleccione **Alternar puntos de interrupción**. Aparecerá un icono rojo en el borde izquierdo superior de la actividad.

   Como alternativa, puede presionar **F9** después de que puede seleccionar la actividad, o haga clic en la actividad y seleccione **punto de interrupción** > **Insertar punto de interrupción** en el menú contextual.

## <a name="see-also"></a>Vea también

- [Cómo: Invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Cómo: Depurar XAML con el Diseñador de flujo de trabajo](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)