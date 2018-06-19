---
title: 'Diseñador de flujo de trabajo: Cómo: establecer puntos de interrupción en flujos de trabajo'
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
ms.openlocfilehash: d2ef863bfb899c218a65673236c284bed63aed11
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973534"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Cómo establecer puntos de interrupción en los flujos de trabajo

Cuando se utiliza el Diseñador de flujo de trabajo de Windows, puede establecer puntos de interrupción en los flujos de trabajo gráficos como lo haría en el código de Visual Basic o C#. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.

 Un punto de interrupción tiene tres estados: *pendiente*, *enlazados*, y *Error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo. Cuando el tiempo de ejecución haya cargado el tipo de flujo de trabajo, pasa a Enlazado. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.

> [!NOTE]
> No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.

> [!WARNING]
> Asegúrese de seleccionar la opción **habilitar solo mi código (sólo administrado)** desde el **herramientas**, **opciones**, **depuración** menú antes de depurar. Si tiene dos secuencias anidadas en otra secuencia y establecer un punto de interrupción en la primera secuencia interna, si presiona **F11** , no se depurará la segunda secuencia interna si el **habilitar solo mi código (sólo administrado)** opción no está seleccionada.

> [!WARNING]
> Los puntos de interrupción de un flujo de trabajo no se alcanzarán si la ruta de acceso completa a la propiedad de archivo XAML no es exacta. La ruta de acceso completa al archivo XAML no es exacta después de mover el proyecto o la solución a otra carpeta o a otro equipo. Presione CTRL+S para guardar y actualizar la ruta de acceso completa.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para establecer un punto de interrupción en una actividad en la vista Diseño

1.  Seleccione la actividad donde desee que se interrumpa el depurador.

2.  En el **depurar** menú, seleccione **Alternar puntos de interrupción**. Aparecerá un icono rojo en el borde izquierdo superior de la actividad.

     Como alternativa, también puede presionar el método abreviado **F9** clave después de que puede seleccionar la actividad o se haga clic en la actividad y seleccione **punto de interrupción** , a continuación, **Insertar punto de interrupción**en el menú contextual.

## <a name="see-also"></a>Vea también

- [Cómo: Invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Cómo: Depurar XAML con el Diseñador de flujo de trabajo](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)