---
title: Depurar flujos de trabajo con el Diseñador de flujo de trabajo
description: Obtenga información sobre cómo el Diseñador de flujo de trabajo proporciona la capacidad de depurar flujos de trabajo y actividades personalizadas con un proceso similar al del depurador predeterminado de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45219da52cdd1ff87b7243c3cc742bb4c97a74e7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435865"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Depurar flujos de trabajo con el Diseñador de flujo de trabajo

El **Diseñador de flujo de trabajo** proporciona la capacidad de depurar flujos de trabajo y actividades personalizadas. El proceso y el comportamiento son similares al del depurador predeterminado de Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Invocar el depurador de flujo de trabajo

Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:

- Seleccione **asociar al proceso** en el menú **depurar** para seleccionar el proceso de host en ejecución para la instancia de flujo de trabajo. Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.

- Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo o para continuar con la ejecución después de que se haya alcanzado un punto de interrupción.

- Usar depuración remota. Para obtener información sobre cómo usar la depuración remota, vea [Cómo: habilitar la depuración remota](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Si la aplicación de flujo de trabajo tiene como destino la arquitectura x86 y se hospeda en un equipo que ejecuta un sistema operativo de 64 bits, la depuración remota no funcionará a menos que Visual Studio esté instalado en el equipo remoto o el destino de la aplicación de flujo de trabajo se cambie a **cualquier CPU**.

## <a name="step-through-code"></a>Examinar el código

- **Paso** a paso por instrucciones: entrar en una actividad presionando **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.

- **Paso a paso para salir:** Salir de una actividad presionando **MAYÚS** + **F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

- **Paso a** paso por procedimientos: desplazarse por una actividad presionando **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

## <a name="debug-with-f5"></a>Depurar con F5

Si va a compilar una aplicación de consola de flujos de trabajo, basta con presionar **F5** para iniciar la depuración en la aplicación y el flujo de trabajo. Si va a crear una biblioteca de actividades por sí misma, debe especificar una aplicación host ejecutable como proyecto de inicio. Para establecer un proyecto de inicio en **Explorador de soluciones** , haga clic con el botón derecho en el nombre del proyecto y seleccione **establecer como proyecto de inicio**.
