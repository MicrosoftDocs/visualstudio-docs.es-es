---
title: Diseñador de flujo de trabajo - depurar flujos de trabajo heredado
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-legacy-workflows"></a>Depurar flujos de trabajo heredados

Si está utilizando el Diseñador de flujo de trabajo heredado de Windows en Visual Studio para compilar aplicaciones de Windows Workflow Foundation (WF) que tienen como destino.NET Framework 3.0 o 3.5, puede depurar los flujos de trabajo como cualquier otro programa estableciendo puntos de interrupción, adjuntar a procesos, y examinar los subprocesos y la pila de llamadas. También tiene la opción de realizar la depuración de forma remota.

> [!NOTE]
> Si varias versiones de Visual Studio se han instalado y desinstalado en el equipo, la depuración de WF3 puede provocar un error con una de las dos posibilidades siguientes:
>
> -   No se alcanzan los puntos de interrupción.
> -   Se mostrará el mensaje siguiente:
>
> **No se puede iniciar la depuración en el servidor web. El depurador no está instalado correctamente.  No se puede depurar el tipo de código solicitado.  Ejecute el programa de instalación para instalar o reparar al depurador.**
>
> Si cualquiera de estos escenarios aparece al depurar los flujos de trabajo de .NET Framework 3.0 o 3.5, realice una reparación de la instalación de Visual Studio.

 Windows Workflow Foundation se integra con las siguientes ventanas de depuración de Visual Studio estándar:

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