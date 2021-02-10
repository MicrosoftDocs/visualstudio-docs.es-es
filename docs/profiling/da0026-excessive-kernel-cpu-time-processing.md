---
title: 'DA0026: Tiempo de procesamiento excesivo de la CPU de kernel | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b1f3231fce4954d3ace5e04e470cda386a9ceebe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936748"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Procesamiento excesivo de tiempo de CPU en modo kernel

|Elemento|Valor|
|-|-|
|Identificador de regla|TODO|
|Categoría|Uso de Herramientas de generación de perfiles|
|Método de generación de perfiles|Muestreo|
|Mensaje|Se midió una cantidad relativamente alta de tiempo de CPU de modo kernel. Considere la posibilidad de investigar el origen con el muestreo de SysCall habilitado.|
|Tipo de regla|Información|

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.

## <a name="cause"></a>Motivo
 El tiempo de CPU proporcional que se ejecutó en modo kernel superó la cantidad de tiempo invertido en modo usuario. Considere la posibilidad de volver a generar perfiles y muestrear el número de llamadas del sistema (syscall) para determinar la causa de los tiempos de ejecución elevados del modo kernel.

## <a name="rule-description"></a>Descripción de la regla
 La proporción relativamente alta de tiempo que la aplicación dedicó a la ejecución del modo kernel merece una mayor investigación. Una aplicación en modo usuario hace una transición al modo kernel para realizar operaciones de E/S, esperar las primitivas de sincronización de subproceso o proceso o realizar llamadas del sistema. Puede investigar los tipos de llamadas del sistema que la aplicación realiza y las funciones que son responsables de dichas llamadas cuando se selecciona la opción para recopilar pilas de llamadas de ejemplo basadas en las llamadas del sistema.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para investigar los tipos de llamadas del sistema que la aplicación realiza, vuelva a ejecutar el perfil y seleccione la opción para recopilar ejemplos basados en las llamadas del sistema. Vea [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md) si está ejecutando las herramientas de generación de perfiles dentro del IDE para obtener más información. Si está ejecutando las herramientas de generación de perfiles desde la línea de comandos, vea la sección **Opciones de intervalo de muestreo** del artículo [VSPerfCmd](../profiling/vsperfcmd.md) en la referencia de herramientas de la línea de comandos de las herramientas de generación de perfiles.
