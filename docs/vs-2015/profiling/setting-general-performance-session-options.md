---
title: Establecer opciones generales de sesión de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b33848b2985cdc4303b75bdc493bfaf33af36b1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256781"
---
# <a name="setting-general-performance-session-options"></a>Establecer opciones generales de sesión de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede establecer el método de recolección y las convenciones de nomenclatura de los datos de generación de perfiles para una sesión de rendimiento de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento. Para abrir este cuadro de diálogo desde el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, a continuación, en **Propiedades**.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Elegir los métodos de recolección de datos  
 El método de recolección base se establece mediante la selección de una opción de **Recolección de generación de perfiles**. Las opciones se describen en la tabla siguiente:  
  
|||  
|-|-|  
|**Muestreo**. El método de muestreo recopila información de generación de perfiles a intervalos regulares. Este método es útil para buscar problemas de utilización del procesador y es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento.|-   [Recopilar estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentación**. El método de instrumentación inserta en una copia de un módulo código de generación de perfiles que graba cada entrada, salida y llamada de función de las funciones del módulo durante una ejecución de generación de perfiles. Este método es útil para recopilar información de tiempo detallada sobre una sección del código y para entender el impacto de las operaciones de entrada y salida en el rendimiento de la aplicación.|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Simultaneidad**. El método de simultaneidad recopila datos de cada evento que bloquea la ejecución del código, como sucede cuando un subproceso espera que se libere el acceso bloqueado a un recurso de aplicación. Este método es útil para analizar aplicaciones multiproceso.|-   [Recopilar datos de simultaneidad de procesos y subprocesos](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Puede recopilar datos de memoria de .NET mediante los métodos de muestreo o instrumentación. El tipo de datos se selecciona en **Generación de perfiles de memoria de .NET**.  
  
|||  
|-|-|  
|**Recopilar información de asignación de objetos .NET**. De forma predeterminada, los datos incluyen el número y el tamaño de los objetos asignados. Active o desactive esta casilla para habilitar o deshabilitar la recolección de datos de memoria de .NET.<br /><br /> **Recopilar también la información de duración de los objetos .NET**. Active esta casilla para incluir datos acerca de las generaciones de recolección de elementos no utilizados que se utilizaron para reclamar los objetos de memoria.|-   [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Al comenzar a generar perfiles de una aplicación, aparece una página de la sesión de generación de perfiles en la que se puede pausar, reanudar y detener la generación de perfiles.  
  
 ![Página de la sesión de generación de perfiles](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>Establecer opciones del archivo de datos de generación de perfiles  
  
|||  
|-|-|  
|**Informe**. De forma predeterminada, el archivo de datos de generación de perfiles (.vsp) recibe el nombre de la aplicación de la que se generan perfiles y se sitúa en la carpeta de la solución o el proyecto. También se anexa al nombre una cadena de fecha y, en los archivos de datos que tendrían nombres duplicados, un número incrementado. Estas opciones se pueden modificar.|-   [Cómo: Establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|



