---
title: Depurar flujos de trabajo heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d15236de90af6a8749482f2b159d66c28a1b8c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-legacy-workflows"></a>Depurar flujos de trabajo heredados
Si usa el [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado en [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para compilar aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino .NET Framework 3.0 o 3.5, puede depurar los flujos de trabajo como cualquier otro programa: establecer puntos de interrupción, adjuntar a procesos y examinar los subprocesos y la pila de llamadas. También tiene la opción de realizar la depuración de forma remota.  
  
> [!NOTE]
>  Si varias versiones de Visual Studio se han instalado y desinstalado en el equipo, la depuración de WF3 puede provocar un error con una de las dos posibilidades siguientes:  
>   
>  -   No se alcanzan los puntos de interrupción.  
> -   Se mostrará el mensaje siguiente:  
>   
>  **No se puede iniciar la depuración en el servidor web. El depurador no está instalado correctamente.  No se puede depurar el tipo de código solicitado.  Ejecute el programa de instalación para instalar o reparar al depurador.**  
>   
>  Si cualquiera de estos escenarios aparece al depurar los flujos de trabajo de .NET Framework 3.0 o 3.5, realice una reparación de la instalación de Visual Studio.  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] se integra con las siguientes ventanas de depuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estándar:  
  
-   **Punto de interrupción**: funciona según lo previsto, pero especificar una actividad para el nombre de función.  
  
-   **Pila de llamadas**: modificado para proporcionar una descripción de las actividades que se han ejecutado en una instancia de flujo de trabajo. Las entradas de la **pila de llamadas** son una búsqueda de prioridad a la profundidad de la ejecución de actividades. Puede hacer doble clic en una entrada para situar el foco en la actividad seleccionada.  
  
-   **Subprocesos**: proporciona el identificador de instancia de la instancia de flujo de trabajo que se está depurando.  
  
 Visual Studio Extensions for Windows Workflow Foundation no admite las siguientes características de depuración:  
  
-   Puntos de interrupción condicionales en la superficie del diseñador  
  
-   Inspección rápida  
  
-   Establecer instrucción siguiente.  
  
-   Ejecutar hasta el cursor.  
  
-   Editar y continuar.  
  
-   Depuración Just-In-Time  
  
-   Depuración en modo mixto  
  
## <a name="in-this-section"></a>En esta sección  
 [Invocar el Depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Deshabilitar el Depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Cómo: Depurar los flujos de trabajo basados en ASP.NET (heredado)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Cómo: Establecer puntos de interrupción en los flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Depurar flujos de trabajo desde un equipo remoto (heredado)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Cómo: Cambiar la opción de ejecución paso a paso de depuración (heredado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)