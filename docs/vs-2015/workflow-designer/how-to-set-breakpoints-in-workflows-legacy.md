---
title: 'Cómo: establecer puntos de interrupción en flujos de trabajo (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603598"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Cómo: Establecer puntos de interrupción en los flujos de trabajo (Heredado)
En este tema se describe cómo establecer puntos de interrupción en aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] compiladas usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando la aplicación [!INCLUDE[wf2](../includes/wf2-md.md)] deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Cuando use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado de [!INCLUDE[vs2010](../includes/vs2010-md.md)] para compilar una aplicación [!INCLUDE[wf2](../includes/wf2-md.md)], puede establecer puntos de interrupción en código C# y Visual Basic de la misma manera que en Visual Studio. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.

 Un punto de interrupción tiene tres Estados: *pendiente*, *enlazado*y *error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo vacío. Cuando el tiempo de ejecución ha cargado el tipo de flujo de trabajo, cambia a Enlazado y se representa mediante un icono rojo sólido. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.

 Puede establecer puntos de interrupción en una actividad de la superficie de diseño de flujo de trabajo de las maneras siguientes:

- Haga clic con el botón secundario en la actividad y seleccione **punto de interrupción \ Insertar punto de interrupción**.

- Seleccione la actividad y presione F9.

- Seleccione **nuevo punto de interrupción** en el menú **depurar** .

     También puede utilizar esta opción para establecer un nuevo punto de interrupción al depurar, si el depurador se detiene en un punto de interrupción.

    > [!NOTE]
    > No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Para establecer un punto de interrupción utilizando la opción Nuevo punto de interrupción del menú Depurar

1. En el menú **depurar** , seleccione **nuevo punto de interrupción**.

2. Haga clic en **interrumpir en función**.

     Se abre el cuadro de diálogo **nuevo punto de interrupción** .

3. Especifique el nombre de una actividad en el cuadro de texto de la **función** con esta sintaxis: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > Opcionalmente, en lugar de usar el nombre de la actividad en el cuadro de texto de la **función** , puede establecer un punto de interrupción especificando la ruta de acceso absoluta de la actividad de flujo de trabajo. Por ejemplo, supongamos que tiene una solución de flujo de trabajo denominada **WorkflowConsoleApplication1** y un flujo de trabajo en la solución denominada **Workflow1** que usa una actividad denominada **Delay1**. Puede usar el nombre de actividad **Delay1** o especificar la ruta de acceso como **Delay1: WorkflowConsoleApplication1. Workflow1** o **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**.

4. Active la casilla **usar IntelliSense** para comprobar el nombre de la función.

     Si esta casilla no está activada, no se realiza ninguna comprobación de nombre de punto de interrupción.

5. Seleccione **flujo de trabajo** en la lista de **idiomas** .

6. Haga clic en **OK**.

## <a name="see-also"></a>Consulte también
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md) [invocar el depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)