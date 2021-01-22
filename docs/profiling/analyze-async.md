---
title: Análisis del rendimiento del código asincrónico de .NET | Microsoft Docs
description: Use la herramienta .NET Async para analizar el rendimiento del código asincrónico. Se calcula el tiempo para cada tarea indicada. Para ver el código, use la opción Ir al archivo de origen.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205494"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Análisis del rendimiento del código asincrónico de .NET

Use la herramienta .NET Async para analizar el rendimiento del código asincrónico en la aplicación.

> [!NOTE]
> La herramienta .NET Async requiere la versión 16.7 de Visual Studio 2019 o posterior y un proyecto de .NET que use **async** y **await**.

## <a name="setup"></a>Programa de instalación

1. Seleccione **Alt + F2** para abrir el generador de perfiles de rendimiento en Visual Studio.

1. Active la casilla **.NET Async**.

   ![Herramienta .NET Async seleccionada](../profiling/media/async-tool-selected.png "Herramienta .NET Async seleccionada")

1. Haga clic en el botón **Iniciar** para ejecutar la herramienta.

1. Una vez que se inicie la ejecución de la herramienta, repase el escenario del que desea generar perfiles en su aplicación. A continuación, seleccione **Detener recopilación** o cierre la aplicación para ver los datos.

1. Una vez que la recopilación se detenga, verá una tabla de las actividades que ocurrieron durante la sesión de generación de perfiles.

   ![Herramienta .NET Async detenida](../profiling/media/async-tool-opened.png "Herramienta .NET Async detenida")

Los eventos asincrónicos se organizan en actividades de manera cronológica. Se muestra cada hora de inicio, hora de finalización y duración.

Cada fila que corresponde a una [tarea](/dotnet/api/system.threading.tasks) se etiqueta en la columna **Nombre**. En el caso de cualquier nombre de tarea que no se pueda resolver, aparecerá una etiqueta **Tarea en**. Después aparece el nombre del método donde ocurrió la tarea. Si no se completa una actividad asincrónica dentro de la sesión de recopilación, aparece una etiqueta **Incompleta** en la columna **Hora de finalización**.

Para investigar más una tarea o actividad específica, haga clic con el botón derecho en la fila. Luego, seleccione **Ir al archivo de origen** para ver en qué parte del código ocurrió esa actividad.

![Herramienta .NET Async con la opción Ir al archivo de origen seleccionada](../profiling/media/async-tool-gotosource.png "Herramienta .NET Async con la opción Ir al archivo de origen seleccionada")

## <a name="see-also"></a>Vea también

- [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md)