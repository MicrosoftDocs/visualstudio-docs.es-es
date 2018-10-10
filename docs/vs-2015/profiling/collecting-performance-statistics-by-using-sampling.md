---
title: Recopilar estadísticas de rendimiento mediante el muestreo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce6a9fed51e4c5dc93fca406dbb43787700d83d2
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880414"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Recopilar estadísticas de rendimiento mediante el muestreo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [recopilar estadísticas de rendimiento mediante el uso de muestreo](https://docs.microsoft.com/visualstudio/profiling/collecting-performance-statistics-by-using-sampling).  
  
De forma predeterminada, el método de muestreo de las herramientas de generación de perfiles [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] recopila información de generación de perfiles cada 10.000.000 ciclos de procesador (aproximadamente cada centésima de segundo en un equipo de 1 GHz). El método de muestreo es útil para buscar problemas de utilización del procesador y es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Puede especificar el método de muestreo mediante uno de los procedimientos siguientes:  
  
-   En la primera página del Asistente de generación de perfiles, haga clic en **Muestreo de la CPU (recomendado)**.  
  
-   En la barra de herramientas **Explorador de rendimiento**, en la lista **Método**, haga clic en **Muestreo**.  
  
-   En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Muestreo**.  
  
## <a name="common-tasks"></a>Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** de la sesión de rendimiento. Para abrir este cuadro de diálogo:  
  
-   En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.  
  
 Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** cuando genere perfiles mediante el método de muestreo.  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|En la página **General**, agregue la colección de los datos de duración y de asignación de memoria de .NET y especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|-   [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Cómo: Establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Muestreo**, cambie la velocidad de muestreo, así como el evento de muestreo de los ciclos de reloj de procesador a otro contador de rendimiento de procesador, o cambie ambos valores.|-   [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md)|  
|En la página **Iniciar**, especifique la aplicación que quiere iniciar, así como el orden de inicio, si tiene varios proyectos .exe en la solución de código.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Interacción de capas**, agregue la información de llamadas de ADO.NET a los datos recopilados en la ejecución de generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Eventos de Windows**, especifique uno o varios eventos de seguimiento de eventos para Windows (ETW) para recopilar con los datos de muestreo.|-   [Cómo: Recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|-   [Cómo: recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzado**, especifique la versión del runtime de .NET Framework de la cual quiere generar el perfil si los módulos de aplicación utilizan varias versiones. De forma predeterminada, se genera el perfil de la primera versión cargada.|-   [Cómo: Especificar el runtime de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



