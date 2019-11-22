---
title: 'How to: Invoke the Workflow Debugger | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292898"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Invocar el depurador de flujo de trabajo
Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:

- Select **Attach to Process** on the **Debug** menu to select the running host process for your workflow instance. Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.

- Press **F5** to start running an instance of the workflow, or to continue to run after a breakpoint has been hit.

- Usar depuración remota. For information on using remote debugging, see [How to: Enable Remote Debugging](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > If the workflow application targets the x86 architecture and is hosted on a machine running a 64 bit operating system, then remote debugging will not work unless [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] is installed on the remote machine or the target for the workflow application is changed to **Any CPU**.

### <a name="stepping-through-code"></a>Ejecución paso a paso del código

- **Step In**: You can step into an activity using **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.

- **Step Out:** You can step out of an activity using **Shift-F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

- **Step Over**: You can step over an activity using **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

### <a name="debugging-with-f5"></a>Depurar con F5

- If you are building a Workflow Console Application project, simply press **F5** to begin debugging into your application and workflow. Si está compilando una biblioteca de actividades por sí sola, es preciso que disponga de una aplicación host ejecutable como proyecto de inicio. To set a startup project in **Solution Explorer**, right-click the project name of the host and select **Set as StartUp Project**.

## <a name="see-also"></a>Vea también
 [How to: Set Breakpoints in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [Debugging Workflows with the Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)