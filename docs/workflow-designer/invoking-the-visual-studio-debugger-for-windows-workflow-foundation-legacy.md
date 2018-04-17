---
title: Invocar el depurador de Visual Studio para Windows Workflow Foundation (heredado) | Documentos de Microsoft
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e3563b175359e00a051138451292eb015958480
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)
Este tema se describe cómo utilizar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador para depurar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicaciones en el Diseñador de flujo de trabajo de Windows heredado. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Generalmente, los flujos de trabajo heredados se depuran de la misma manera que los programas escritos en otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation de las formas siguientes:

-   Seleccione **adjuntar al proceso** en el **depurar** menú para seleccionar una instancia de flujo de trabajo de ejecución de los procesos disponibles.

-   Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo, o continúe ejecutándose una vez que se ha alcanzado un punto de interrupción.

## <a name="stepping-through-code"></a>Ejecución paso a paso del código
 El depurador admite uno de los procedimientos de depuración más comunes, la ejecución paso a paso, es decir, la ejecución del código de línea en línea. Hay tres comandos para ejecutar el código paso a paso:

-   **En el paso**: puede ir a una actividad usando **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución. ENTRAR en los controladores de código desde el diseñador no se admite para las actividades siguientes: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, o **ReplicatorActivity**. Para depurar los controladores asociados a estas actividades, debe colocar puntos de interrupción explícitos en el código.

-   **Paso a paso fuera**: puede ejecutar paso a paso de una actividad presionando **MAYÚS + F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

-   **Paso a paso por**: puede saltarse una actividad usando **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta. las interrupciones del depurador en el primer elemento secundario ejecutable de la actividad compuesta. Cuando la ejecución paso a paso a través no compuestas, como un **CodeActivity** actividad, el depurador ejecuta la actividad y sus controladores asociados y los saltos en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

## <a name="attaching-to-a-process"></a>Adjuntar a un proceso
 Para depurar un flujo de trabajo adjuntando a un proceso, seleccione el proceso disponible en la **procesos disponibles** cuadro de lista en la **adjuntar al proceso** cuadro de diálogo. Si **automático: código de flujo de trabajo** no se muestra en el **adjuntar a** texto cuadro, a continuación, haga clic en **seleccione**. En el **Seleccionar tipo de código** cuadro de diálogo, haga clic en **depurar estos tipos de código** y seleccione **flujo de trabajo**. A continuación, haga clic en **Aceptar** y haga clic en **adjuntar**.

## <a name="debugging-with-f5"></a>Depurar con F5
 Si una aplicación de host de flujo de trabajo y flujo de trabajo DLL se encuentran en distintos proyectos de Visual Studio, por ejemplo, cuando se usa una biblioteca de actividades de flujo de trabajo, debe establecer el proyecto DLL de flujo de trabajo como proyecto de inicio de la solución Visual Studio para depurar el flujo de trabajo usar **F5**. También debe establecer la ruta de acceso a la aplicación host en el proyecto DLL de flujo de trabajo **iniciar programa externo** propiedad.

 Para establecer un proyecto de inicio en el Explorador de soluciones, haga clic en el nombre del proyecto y seleccione **establecer como proyecto de inicio**. Para establecer la ruta de acceso al host en el **iniciar programa externo** propiedad, haga doble clic en el proyecto de flujo de trabajo **propiedades** nodo en el Explorador de soluciones y seleccione el **depurar** pestaña. En **acción de inicio**, seleccione **programa externo de inicio** y escriba la ruta de acceso al archivo .exe que hospeda el flujo de trabajo que desea depurar.

 Si la aplicación host se establece como proyecto de inicio, sólo se invoca el depurador de Visual Studio para depurar, y no se invoca el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation. Si se utiliza el depurador de Visual Studio, sólo se alcanzan los puntos de interrupción del código de C# o Visual Basic, pero no los puntos de interrupción establecidos en el diseñador de flujo de trabajo. Por ejemplo, se utiliza un punto de interrupción establecido en una actividad <xref:System.Workflow.Activities.ParallelActivity> en el diseñador si se utiliza el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation, pero no si se utiliza el depurador de Visual Studio.

## <a name="see-also"></a>Vea también

- [Cómo: Establecer puntos de interrupción en los flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)