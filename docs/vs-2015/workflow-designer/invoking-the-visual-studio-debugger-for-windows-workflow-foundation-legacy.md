---
title: Invocar el depurador para Windows Workflow Foundation (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658980"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)
En este tema se describe cómo usar el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para depurar aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Generalmente, los flujos de trabajo heredados se depuran de la misma manera que los programas escritos en otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] for Windows Workflow Foundation de las formas siguientes:

- Seleccione **asociar al proceso** en el menú **depurar** para seleccionar una instancia de flujo de trabajo en ejecución en los procesos disponibles.

- Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo o para continuar con la ejecución después de que se haya alcanzado un punto de interrupción.

## <a name="stepping-through-code"></a>Ejecución paso a paso del código
 El depurador admite uno de los procedimientos de depuración más comunes, la ejecución paso a paso, es decir, la ejecución del código de línea en línea. Hay tres comandos para ejecutar el código paso a paso:

- **Paso en**: puede entrar en una actividad mediante **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución. La ejecución paso a paso de los controladores de código desde el diseñador no es compatible con las actividades siguientes: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**o **ReplicatorActivity**. Para depurar los controladores asociados a estas actividades, debe colocar puntos de interrupción explícitos en el código.

- **Paso a paso para salir**: puede salir de una actividad mediante **Shift-F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

- **Paso a paso por procedimientos**: puede recorrer una actividad mediante **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta. las interrupciones del depurador en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a través de un objeto no compuesto, como una actividad **CodeActivity** , el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

## <a name="attaching-to-a-process"></a>Adjuntar a un proceso
 Para depurar un flujo de trabajo adjuntando a un proceso, seleccione el proceso disponible en el cuadro de lista **procesos disponibles** del cuadro de diálogo **asociar al proceso** . Si es **automático: el código de flujo de trabajo** no se muestra en el cuadro de texto **adjuntar a** , haga clic en **seleccionar**. En el cuadro de diálogo **Seleccionar tipo de código** , haga clic en **depurar estos tipos de código** y seleccione **flujo de trabajo**. A continuación, haga clic en **Aceptar** y en **asociar**.

## <a name="debugging-with-f5"></a>Depurar con F5
 Si una aplicación host de flujo de trabajo y un archivo DLL de flujo de trabajo se encuentran en distintos proyectos de Visual Studio, por ejemplo, cuando se usa una biblioteca de actividades de flujo de trabajo, debe establecer el proyecto DLL de flujo de trabajo como proyecto de inicio de la solución de Visual Studio para depurar el flujo de trabajo. usar **F5**. También debe establecer la ruta de acceso a la aplicación host en la propiedad **programa externo de inicio** del proyecto dll del flujo de trabajo.

 Para establecer un proyecto de inicio en Explorador de soluciones, haga clic con el botón derecho en el nombre del proyecto y seleccione **establecer como proyecto de inicio**. Para establecer la ruta de acceso al host en la propiedad **programa externo de inicio** , haga doble clic en el nodo **propiedades** del proyecto de flujo de trabajo en explorador de soluciones y seleccione la pestaña **depurar** . En **acción de inicio**, seleccione **programa externo de inicio** y escriba la ruta de acceso al archivo. exe que hospeda el flujo de trabajo que desea depurar.

 Si la aplicación host se establece como proyecto de inicio, sólo se invoca el depurador de Visual Studio para depurar, y no se invoca el depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] for Windows Workflow Foundation. Si se utiliza el depurador de Visual Studio, sólo se alcanzan los puntos de interrupción del código de C# o Visual Basic, pero no los puntos de interrupción establecidos en el diseñador de flujo de trabajo. Por ejemplo, se utiliza un punto de interrupción establecido en una actividad <xref:System.Workflow.Activities.ParallelActivity> en el diseñador si se utiliza el depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] for Windows Workflow Foundation, pero no si se utiliza el depurador de Visual Studio.

## <a name="see-also"></a>Vea también
 [Cómo: establecer puntos de interrupción en flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)