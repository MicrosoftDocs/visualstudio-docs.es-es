---
title: Descripción de los métodos de recopilación de rendimiento del generador de perfiles
description: Obtenga información sobre los métodos de recopilación de datos que usan las herramientas dentro del Generador de perfiles de rendimiento de Visual Studio.
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
ms.openlocfilehash: e34fd78d7ff44aeffc4ca4d61c84a0a9af6747a5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722274"
---
# <a name="understand-profiler-performance-collection-methods"></a>Descripción de los métodos de recopilación de rendimiento del generador de perfiles

En este documento se describen los métodos de recopilación de datos que utilizan las herramientas dentro del Generador de perfiles de rendimiento de Visual Studio. 

## <a name="sampling"></a>Muestreo

Los métodos de muestreo de generación de perfiles recopilan datos estadísticos sobre el trabajo realizado por una aplicación durante una generación de perfiles. La recopilación de datos se realiza mediante la recopilación de información de la aplicación a intervalos regulares o según una frecuencia de muestreo, como cada milisegundo, y analizando después estos datos para crear un modelo del tiempo dedicado a la aplicación. El método de muestreo consume pocos recursos y afecta poco a la ejecución de la aplicación de la cual se generan perfiles. Las herramientas del Generador de perfiles de rendimiento que usan el método de muestreo incluyen la herramienta [Uso de CPU](../profiling/cpu-usage.md).

## <a name="instrumentation"></a>Instrumentación

La generación de perfiles de instrumentación recopila información detallada sobre el trabajo realizado por una aplicación durante una de generación de perfiles. La recopilación de datos se realiza mediante herramientas que insertan código en un archivo binario que captura información de tiempo o mediante enlaces de devolución de llamada para recopilar y emitir la información exacta de tiempo y recuento de llamadas mientras se ejecuta una aplicación. El método de instrumentación tiene una sobrecarga alta en comparación con los enfoques basados en el muestreo. Las herramientas del Generador de perfiles de rendimiento que usan la instrumentación incluyen la herramienta [Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md).