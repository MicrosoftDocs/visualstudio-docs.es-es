---
title: Establecer opciones generales de sesión de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5268e6821714dc6850541c319dba450bcc04490b
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263565"
---
# <a name="set-general-performance-session-options"></a>Establecimiento de opciones generales de sesión de rendimiento

Puede establecer el método de recolección y las convenciones de nomenclatura de los datos de generación de perfiles para una sesión de rendimiento de las Herramientas de generación de perfiles de Visual Studio en la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento. Para abrir este cuadro de diálogo desde el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, a continuación, en **Propiedades**.

## <a name="choosing-data-collection-methods"></a>Elección de los métodos de recopilación de datos

El método de recolección base se establece mediante la selección de una opción de **Recolección de generación de perfiles**. Las opciones se describen en la tabla siguiente:

|||
|-|-|
|**Muestreo**. El método de muestreo recopila información de generación de perfiles a intervalos regulares. Este método es útil para buscar problemas de utilización del procesador y es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento.|- [Recopilar estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentación**. El método de instrumentación inserta en una copia de un módulo código de generación de perfiles que graba cada entrada, salida y llamada de función de las funciones del módulo durante una ejecución de generación de perfiles. Este método es útil para recopilar información de tiempo detallada sobre una sección del código y para entender el impacto de las operaciones de entrada y salida en el rendimiento de la aplicación.|- [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Simultaneidad**. El método de simultaneidad recopila datos de cada evento que bloquea la ejecución del código, como sucede cuando un subproceso espera que se libere el acceso bloqueado a un recurso de aplicación. Este método es útil para analizar aplicaciones multiproceso.|- [Recopilar datos de simultaneidad de procesos y subprocesos](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Puede recopilar datos de memoria de .NET mediante los métodos de muestreo o instrumentación. El tipo de datos se selecciona en **Generación de perfiles de memoria de .NET**.

|||
|-|-|
|**Recopilar información de asignación de objetos .NET**. De forma predeterminada, los datos incluyen el número y el tamaño de los objetos asignados. Active o desactive esta casilla para habilitar o deshabilitar la recolección de datos de memoria de .NET. |- [Recopilar datos de duración y de asignación de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Recopilar también la información de duración de los objetos .NET**. Active esta casilla para incluir datos acerca de las generaciones de recolección de elementos no utilizados que se utilizaron para reclamar los objetos de memoria.|- [Recopilar datos de duración y de asignación de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  |

 Al comenzar a generar perfiles de una aplicación, aparece una página de la sesión de generación de perfiles en la que se puede pausar, reanudar y detener la generación de perfiles.

 ![Página de la sesión de generación de perfiles](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Establecimiento de opciones del archivo de datos de generación de perfiles

|||
|-|-|
|**Informe**. De forma predeterminada, el archivo de datos de generación de perfiles (.vsp) recibe el nombre de la aplicación de la que se generan perfiles y se sitúa en la carpeta de la solución o el proyecto. También se anexa al nombre una cadena de fecha y, en los archivos de datos que tendrían nombres duplicados, un número incrementado. Estas opciones se pueden modificar.|- [Cómo: Establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|