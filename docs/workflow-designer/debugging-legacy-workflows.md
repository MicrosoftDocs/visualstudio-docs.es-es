---
title: Depurar flujos de trabajo heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4898e8f720143bd60337c9fe6bed20a7489c0d04
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-legacy-workflows"></a>Depurar flujos de trabajo heredados

Si está utilizando el Diseñador de flujo de trabajo de Windows heredado en [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para generar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] las aplicaciones que tienen como destino.NET Framework 3.0 o 3.5, puede depurar los flujos de trabajo como cualquier otro programa: establecer puntos de interrupción, adjuntar a procesos y examinar subprocesos y la pila de llamadas. También tiene la opción de realizar la depuración de forma remota.

> [!NOTE]
> Si varias versiones de Visual Studio se han instalado y desinstalado en el equipo, la depuración de WF3 puede provocar un error con una de las dos posibilidades siguientes:
>
> -   No se alcanzan los puntos de interrupción.
> -   Se mostrará el mensaje siguiente:
>
> **No se puede iniciar la depuración en el servidor web. El depurador no está instalado correctamente.  No se puede depurar el tipo de código solicitado.  Ejecute el programa de instalación para instalar o reparar al depurador.**
>
> Si cualquiera de estos escenarios aparece al depurar los flujos de trabajo de .NET Framework 3.0 o 3.5, realice una reparación de la instalación de Visual Studio.

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