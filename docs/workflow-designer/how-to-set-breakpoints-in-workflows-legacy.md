---
title: 'Diseñador de flujo de trabajo: Cómo: establecer puntos de interrupción en flujos de trabajo (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c70b630404830fa8c733a7310e4700da8f08b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Cómo: Establecer puntos de interrupción en los flujos de trabajo (Heredado)

En este tema se describe cómo establecer puntos de interrupción en Windows Workflow Foundation (WF) y las aplicaciones creadas mediante el Diseñador de flujo de trabajo de Windows heredadas. Use el Diseñador de flujo de trabajo heredado cuando la aplicación de Windows Workflow Foundation debe tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

 Al utilizar el Diseñador de flujo de trabajo heredados en Visual Studio 2010 para crear una aplicación de Windows Workflow Foundation, puede establecer puntos de interrupción en código C# y Visual Basic como se hace en Visual Studio. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.

 Un punto de interrupción tiene tres estados: *pendiente*, *enlazados*, y *Error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo vacío. Cuando el tiempo de ejecución ha cargado el tipo de flujo de trabajo, cambia a Enlazado y se representa mediante un icono rojo sólido. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.

 Puede establecer puntos de interrupción en una actividad de la superficie de diseño de flujo de trabajo de las maneras siguientes:

-   Haga clic en la actividad y seleccione **punto de interrupción \ Insertar punto de interrupción**.

-   Seleccione la actividad y presione F9.

-   Seleccione **nuevo punto de interrupción** desde el **depurar** menú.

     También puede utilizar esta opción para establecer un nuevo punto de interrupción al depurar, si el depurador se detiene en un punto de interrupción.

    > [!NOTE]
    > No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Para establecer un punto de interrupción utilizando la opción Nuevo punto de interrupción del menú Depurar

1.  En el **depurar** menú, seleccione **nuevo punto de interrupción**.

2.  Haga clic en **interrumpir en una función**.

     El **nuevo punto de interrupción** abre el cuadro de diálogo.

3.  Especifique el nombre de una actividad en el **función** cuadro de texto con esta sintaxis: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Si lo desea, en lugar de usar el nombre de la actividad en el **función** cuadro de texto, puede establecer un punto de interrupción especificando la ruta de acceso absoluta de la actividad de flujo de trabajo. Por ejemplo, suponga que tiene una solución de flujo de trabajo denominada **WorkflowConsoleApplication1** y un flujo de trabajo en la solución denominado **Workflow1** que usa una actividad denominada **Delay1**. Puede usar el nombre de la actividad **Delay1** o especifique la ruta de acceso como **Delay1:WorkflowConsoleApplication1.Workflow1** o **Delay1:WorkflowConsoleApplication1.Workflow1: {} 6614886A-608E-412B-BF98-99FF1559DDDF}**.

4.  Seleccione el **usar IntelliSense** casilla de verificación para comprobar el nombre de función.

     Si esta casilla no está activada, no se realiza ninguna comprobación de nombre de punto de interrupción.

5.  Seleccione **flujo de trabajo** desde el **lenguaje** lista.

6.  Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)
- [Invocar el Depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)