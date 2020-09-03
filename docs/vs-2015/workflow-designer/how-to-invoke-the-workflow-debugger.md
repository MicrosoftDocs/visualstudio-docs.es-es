---
title: 'Cómo: invocar el depurador de flujo de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849268"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Invocar el depurador de flujo de trabajo
Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:

- Seleccione **asociar al proceso** en el menú **depurar** para seleccionar el proceso de host en ejecución para la instancia de flujo de trabajo. Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.

- Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo o para continuar con la ejecución después de que se haya alcanzado un punto de interrupción.

- Usar depuración remota. Para obtener información sobre cómo usar la depuración remota, vea [Cómo: habilitar la depuración remota](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > Si la aplicación de flujo de trabajo tiene como destino la arquitectura x86 y se hospeda en un equipo que ejecuta un sistema operativo de 64 bits, la depuración remota no funcionará a menos que [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] esté instalado en el equipo remoto o el destino de la aplicación de flujo de trabajo se cambie a **cualquier CPU**.

### <a name="stepping-through-code"></a>Ejecución paso a paso del código

- **Paso en**: puede entrar en una actividad mediante **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.

- **Paso a paso para salir:** Puede salir de una actividad mediante **Shift-F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

- **Paso a paso por procedimientos**: puede recorrer una actividad mediante **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

### <a name="debugging-with-f5"></a>Depurar con F5

- Si va a compilar un proyecto de aplicación de consola de flujos de trabajo, simplemente presione **F5** para iniciar la depuración en la aplicación y el flujo de trabajo. Si está compilando una biblioteca de actividades por sí sola, es preciso que disponga de una aplicación host ejecutable como proyecto de inicio. Para establecer un proyecto de inicio en **Explorador de soluciones**, haga clic con el botón derecho en el nombre del proyecto y seleccione **establecer como proyecto de inicio**.

## <a name="see-also"></a>Consulte también
 [Cómo: establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [Depurar flujos de trabajo con el diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
