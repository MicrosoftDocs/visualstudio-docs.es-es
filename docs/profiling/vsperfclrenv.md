---
title: VSPerfCLREnv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 629e810bd05fe838e18cc78587921266c351f32d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

La herramienta VSPerfCLREnv se usa para establecer las variables de entorno necesarias para generar perfiles de una aplicación de .NET Framework. Utiliza la siguiente sintaxis:

```
VsPerfCLREnv [/option]
```

La opción que elija depende de cuál de los tres tipos de generación de perfiles utilice: muestreo, instrumentación o global. Es necesaria una opción independiente para incluir datos de interacción de capas en los datos de generación de perfiles. La sintaxis de cada opción se describe en las siguientes tablas.

> [!NOTE]
> Cuando haya terminado de generar de perfiles, ejecute **VSPerfCLREnv** con la opción **/off** o **/globaloff** para eliminar las variables de entorno necesarias para la generación de perfiles. Para obtener más información, consulte Opciones de VSPerfCLREnv para eliminar la configuración del entorno.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Opciones de VSPerfCLREnv para incluir datos de interacción de capas

> [!WARNING]
> La generación de perfiles de interacción de capas se puede recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.

La generación de perfiles de interacción de capas proporciona información adicional sobre las consultas ADO.NET en aplicaciones de varios niveles. Los datos se recopilan solamente para las llamadas a funciones sincrónicas. Los datos de interacción se pueden agregar a cualquier proceso de generación de perfiles mediante cualquier método de generación de perfiles.

Las opciones **InteractionOn** y **GlobalInteractionOn** habilitan la recopilación de datos de interacción de capas. La opción de interacción debe establecerse después de establecer la variable de entorno VSPerfCLREnv necesaria para generar perfiles de una aplicación.

En el siguiente ejemplo se incluyen datos de interacción de capas en un proceso de generación de perfiles que usa el método de muestreo:

```
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

En el siguiente ejemplo se incluyen datos de interacción de capas en un proceso de generación de perfiles para un servicio de Windows:

```
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Opciones de VSPerfCLREnv para la generación de perfiles de instrumentación de procesos

En la siguiente tabla se describen las opciones de VSPerfCLREnv para la generación de perfiles de instrumentación:

|Opción|Description|
|------------|-----------------|
|**TraceOn**|Permite generar perfiles mediante el método de instrumentación. No permite la generación de perfiles de asignación de memoria o recopilar datos de duración de objetos.|
|**TraceGC**|Permite generar perfiles de asignación de memoria mediante el método de instrumentación. No permite recopilar datos de duración de objetos.|
|**TraceGCLife**|Permite la generación de perfiles de asignación de memoria y recopilar datos de duración de objetos mediante el método de instrumentación.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Opciones de VSPerfCLREnv para la generación de perfiles de muestreo de procesos

En la siguiente tabla se describen las opciones de VSPerfCLREnv para la generación de perfiles de muestreo:

|Opción|Description|
|------------|-----------------|
|**SampleOn**|Permite generar perfiles mediante el método de muestreo. No permite la generación de perfiles de asignación de memoria o recopilar datos de duración de objetos.|
|**SampleGC**|Permite generar perfiles de asignación de memoria mediante el método de muestreo. No permite recopilar datos de duración de objetos.|
|**SampleGCLife**|Permite generar perfiles de asignación de memoria mediante el método de muestreo. También permite recopilar datos de duración de objetos.|
|**SampleLineOff**|Deshabilita la recopilación de datos de generación de perfiles en el nivel de línea. NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Opciones de VSPerfCLREnv para la generación de perfiles Global

Para generar perfiles de un servicio administrado como una aplicación web ASP.NET que inicia el sistema operativo en lugar del usuario, utilice las opciones de generación de perfiles global de las opciones de VSPerfCLREnv. En la siguiente tabla se describen las versiones globales de las opciones de VSPerfCLREnv. Estas opciones establecen las variables de entorno adecuadas en el registro.

|Opción|Description|
|------------|-----------------|
|**GlobalTraceOn**|Permite generar perfiles globales mediante el método de instrumentación. No recopila eventos de asignación de memoria ni datos de duración de objetos.|
|**GlobalTraceGC**|Permite generar perfiles de asignación de memoria globales mediante el método de instrumentación. No permite recopilar datos de duración de objetos.|
|**GlobalTraceGCLife**|Permite generar perfiles de asignación de memoria globales mediante el método de instrumentación. También permite la recopilación de datos de duración de objetos.|
|**GlobalSampleOn**|Permite generar perfiles globales mediante el método de muestreo. No permite recopilar eventos de asignación de memoria ni datos de duración de objetos.|
|**GlobalSampleGC**|Permite generar perfiles de asignación de memoria global mediante el método de muestreo. No permite recopilar datos de duración de objetos.|
|**GlobalSampleGCLife**|Permite generar perfiles de asignación de memoria global mediante el método de muestreo. También permite recopilar datos de duración de objetos.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Opciones de VSPerfCLREnv para eliminar la configuración de entorno

 Cuando haya terminado de generar perfiles de la aplicación administrada, utilice una de las siguientes opciones para eliminar las variables de entorno que agregó VSPerfCLREnv. En la siguiente tabla se describe cómo eliminar las variables de entorno estándar y globales:

|Opción|Description|
|------------|-----------------|
|**Off**|Elimina las variables de entorno de generación de perfiles de .NET estándar. Utilice esta opción cuando se hayan utilizado las opciones de VSPerfClrEnv que no sean globales para establecer las variables de entorno del generador de perfiles.|
|**GlobalOff**|Elimina las variables de entorno de generación de perfiles de .NET global. Utilice esta opción cuando el sistema operativo, y no el generador de perfiles, haya iniciado la aplicación.|

## <a name="remarks"></a>Comentarios

Estas opciones no son necesarias para la generación de perfiles de una aplicación administrada si la aplicación se inicia mediante el explorador de rendimiento en el IDE. El explorador de rendimiento establece toda la configuración de entorno necesaria en su lugar.

Si no se estableció el entorno correcto durante el proceso de generación de perfiles, se emite una advertencia durante el análisis y los nombres de la función administrada no se resolverán correctamente.

## <a name="see-also"></a>Vea también

[Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)