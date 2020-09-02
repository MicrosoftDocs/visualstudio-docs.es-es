---
title: Depuración de flujos de trabajo heredados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656859"
---
# <a name="debugging-legacy-workflows"></a>Depurar flujos de trabajo heredados
Si usa el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado en [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] para compilar aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino .NET Framework 3.0 o 3.5, puede depurar los flujos de trabajo como cualquier otro programa: establecer puntos de interrupción, adjuntar a procesos y examinar los subprocesos y la pila de llamadas. También tiene la opción de realizar la depuración de forma remota.

> [!NOTE]
> Si varias versiones de Visual Studio se han instalado y desinstalado en el equipo, la depuración de WF3 puede provocar un error con una de las dos posibilidades siguientes:
>
> - No se alcanzan los puntos de interrupción.
>   - Se muestra el mensaje siguiente:
>
>   **No se puede iniciar la depuración en el servidor Web. El depurador no está instalado correctamente.  No se puede depurar el tipo de código solicitado.  Ejecute el programa de instalación para instalar o reparar el depurador.**
>
>   Si cualquiera de estos escenarios aparece al depurar los flujos de trabajo de .NET Framework 3.0 o 3.5, realice una reparación de la instalación de Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] se integra con las siguientes ventanas de depuración de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estándar:

- **Punto de interrupción**: funciona según lo previsto, pero se especifica una actividad para el nombre de la función.

- **Pila de llamadas**: se ha modificado para proporcionar un esquema de las actividades que se han ejecutado en una instancia de flujo de trabajo. Las entradas de la ventana **pila de llamadas** son una búsqueda con prioridad a la profundidad de las actividades en ejecución. Puede hacer doble clic en una entrada para situar el foco en la actividad seleccionada.

- **Subprocesos**: proporciona el ID. de instancia de la instancia de flujo de trabajo que se está depurando.

  Visual Studio Extensions for Windows Workflow Foundation no admite las siguientes características de depuración:

- Puntos de interrupción condicionales en la superficie del diseñador

- Inspección rápida.

- Establecer instrucción siguiente.

- Ejecutar hasta el cursor.

- Editar y continuar.

- Depuración Just-In-Time

- Depuración en modo mixto

## <a name="in-this-section"></a>En esta sección
 [Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Deshabilitar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Cómo: Depurar los flujos de trabajo basados en ASP.NET (Heredado)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Cómo: Establecer puntos de interrupción en los flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Depurar flujos de trabajo desde un equipo remoto (Heredado)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)

 [Cómo: Cambiar la opción de ejecución paso a paso de depuración (Heredado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)