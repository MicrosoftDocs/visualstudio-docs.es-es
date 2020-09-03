---
title: 'Diseñador de flujo de trabajo: Cómo establecer puntos de interrupción en los flujos de trabajo'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9530e7ec018a89c3648f61660a5651eddaace805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817494"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Cómo: establecer puntos de interrupción en flujos de trabajo

Al usar Diseñador de flujo de trabajo, puede establecer puntos de interrupción en los flujos de trabajo gráficos como haría en Visual Basic o en el código de C#. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.

Un punto de interrupción tiene tres Estados: *pendiente*, *enlazado*y *error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo. Cuando el tiempo de ejecución haya cargado el tipo de flujo de trabajo, pasa a Enlazado. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.

> [!NOTE]
> No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.

> [!NOTE]
> Asegúrese de seleccionar la opción **Habilitar solo mi código (solo administrado)** en el menú de **Tools**  >  **Options**  >  **depuración** opciones de herramientas antes de depurar. Si la opción no está seleccionada y tiene dos secuencias anidadas dentro de otra, y establece un punto de interrupción en la primera secuencia interna, al presionar **F11** no se depurará en la segunda secuencia interna.

> [!NOTE]
> No se alcanzan los puntos de interrupción en un flujo de trabajo si la ruta de acceso completa a la propiedad del archivo XAML no es exacta. La ruta de acceso completa al archivo XAML no es exacta después de mover el proyecto o la solución a otra carpeta o a otra máquina. Seleccione **Ctrl** + **S** para guardar y actualizar la propiedad ruta de acceso completa.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para establecer un punto de interrupción en una actividad en la vista Diseño

1. Seleccione la actividad donde desee que se interrumpa el depurador.

2. En el menú **depurar** , seleccione **alternar punto de interrupción**. Aparecerá un icono rojo en el borde izquierdo superior de la actividad.

   Como alternativa, puede presionar **F9** después de seleccionar la actividad, o puede hacer clic con el botón secundario en la actividad y seleccionar **punto**  >  de interrupción**Insertar punto de interrupción** en el menú contextual.

## <a name="see-also"></a>Consulte también

- [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Depurar XAML con el Diseñador de flujo de trabajo](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
