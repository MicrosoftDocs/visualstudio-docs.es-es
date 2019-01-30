---
title: Recopilar estadísticas de rendimiento mediante el muestreo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d84af066a7d267c4fca6af206d6ff7c064f744e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917151"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Recopilar estadísticas de rendimiento mediante el muestreo

De manera predeterminada, el método de muestreo de las Herramientas de generación de perfiles de Visual Studio recopila información de generación de perfiles cada 10.000.000 ciclos de procesador (aproximadamente cada centésima de segundo en un equipo de 1 GHz). El método de muestreo es útil para buscar problemas de utilización del procesador y es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Puede especificar el método de muestreo mediante uno de los procedimientos siguientes:

- En la primera página del Asistente de generación de perfiles, haga clic en **Muestreo de la CPU (recomendado)**.
- En la barra de herramientas **Explorador de rendimiento**, en la lista **Método**, haga clic en **Muestreo**.
- En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Muestreo**.

## <a name="common-tasks"></a>Tareas comunes

Puede especificar opciones adicionales en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** de la sesión de rendimiento. Para abrir este cuadro de diálogo:

- En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.

  Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** cuando genere perfiles mediante el método de muestreo.

|Tarea|Contenido relacionado|
|----------|---------------------|
|En la página **General**, agregue la colección de los datos de duración y de asignación de memoria de .NET y especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|- [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Cómo: Establecimiento de opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|
|En la página **Muestreo**, cambie la velocidad de muestreo, así como el evento de muestreo de los ciclos de reloj de procesador a otro contador de rendimiento de procesador, o cambie ambos valores.|- [Cómo: Elección de eventos de muestreo](../profiling/how-to-choose-sampling-events.md)|
|En la página **Iniciar**, especifique la aplicación que quiere iniciar, así como el orden de inicio, si tiene varios proyectos .exe en la solución de código.|- [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|
|En la página **Interacción de capas**, agregue la información de llamadas de ADO.NET a los datos recopilados en la ejecución de generación de perfiles.|- [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|
|En la página **Eventos de Windows**, especifique uno o varios eventos de seguimiento de eventos para Windows (ETW) para recopilar con los datos de muestreo.|- [Cómo: Recopilación de datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|- [Cómo: Recopilación de datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|
|En la página **Avanzado**, especifique la versión del runtime de .NET Framework de la cual quiere generar el perfil si los módulos de aplicación utilizan varias versiones. De forma predeterminada, se genera el perfil de la primera versión cargada.|- [Cómo: Especificación del entorno de ejecución de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|