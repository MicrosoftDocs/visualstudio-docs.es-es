---
title: Descripción de los métodos de recopilación de rendimiento del generador de perfiles
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f0e24f3fc33ea456ad02bf9797b934a1a56d4492
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238587"
---
# <a name="understand-profiler-performance-collection-methods"></a>Descripción de los métodos de recopilación de rendimiento del generador de perfiles

En este documento se describen los métodos de recopilación de datos que utilizan las herramientas dentro del Generador de perfiles de rendimiento de Visual Studio. 

## <a name="sampling"></a>Muestreo

Los métodos de muestreo de generación de perfiles recopilan datos estadísticos sobre el trabajo realizado por una aplicación durante una generación de perfiles. La recopilación de datos se realiza mediante la recopilación de información de la aplicación a intervalos regulares o según una frecuencia de muestreo, como cada milisegundo, y analizando después estos datos para crear un modelo del tiempo dedicado a la aplicación. El método de muestreo consume pocos recursos y afecta poco a la ejecución de la aplicación de la cual se generan perfiles. Las herramientas del Generador de perfiles de rendimiento que usan el método de muestreo incluyen la herramienta [Uso de CPU](../profiling/cpu-usage.md).

## <a name="instrumentation"></a>Instrumentación

La generación de perfiles de instrumentación recopila información detallada sobre el trabajo realizado por una aplicación durante una de generación de perfiles. La recopilación de datos se realiza mediante herramientas que insertan código en un archivo binario que captura información de tiempo o mediante enlaces de devolución de llamada para recopilar y emitir la información exacta de tiempo y recuento de llamadas mientras se ejecuta una aplicación. El método de instrumentación tiene una sobrecarga alta en comparación con los enfoques basados en el muestreo. Las herramientas del Generador de perfiles de rendimiento que usan la instrumentación incluyen la herramienta [Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md).