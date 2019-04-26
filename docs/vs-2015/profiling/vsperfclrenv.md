---
title: VSPerfCLREnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: afee2c56a7f29d50f46c7cbb734bc0297223845c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446689"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta VSPerfCLREnv se usa para establecer las variables de entorno necesarias para generar perfiles de una aplicación de .NET Framework. Utiliza la siguiente sintaxis:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 La opción que elija depende de cuál de los tres tipos de generación de perfiles utilice: muestreo, instrumentación o global. Es necesaria una opción independiente para incluir datos de interacción de capas en los datos de generación de perfiles. La sintaxis de cada opción se describe en las siguientes tablas.  
  
> [!NOTE]
> Cuando haya terminado de generar de perfiles, ejecute **VSPerfCLREnv** con la opción **/off** o **/globaloff** para eliminar las variables de entorno necesarias para la generación de perfiles. Para obtener más información, consulte Opciones de VSPerfCLREnv para eliminar la configuración del entorno.  
  
 **Opciones de VSPerfCLREnv para incluir datos de interacción de capas**  
  
> [!WARNING]
> La generación de perfiles de interacción de capas se puede recopilar usando [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] y [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
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
  
 **Opciones de VSPerfCLREnv para la generación de perfiles de instrumentación de procesos**  
  
 En la siguiente tabla se describen las opciones de VSPerfCLREnv para la generación de perfiles de instrumentación:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**TraceOn**|Permite generar perfiles mediante el método de instrumentación. No permite la generación de perfiles de asignación de memoria o recopilar datos de duración de objetos.|  
|**TraceGC**|Permite generar perfiles de asignación de memoria mediante el método de instrumentación. No permite recopilar datos de duración de objetos.|  
|**TraceGCLife**|Permite la generación de perfiles de asignación de memoria y recopilar datos de duración de objetos mediante el método de instrumentación.|  
  
 **Opciones de VSPerfCLREnv para la generación de perfiles de muestreo de procesos**  
  
 En la siguiente tabla se describen las opciones de VSPerfCLREnv para la generación de perfiles de muestreo:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**SampleOn**|Permite generar perfiles mediante el método de muestreo. No permite la generación de perfiles de asignación de memoria o recopilar datos de duración de objetos.|  
|**SampleGC**|Permite generar perfiles de asignación de memoria mediante el método de muestreo. No permite recopilar datos de duración de objetos.|  
|**SampleGCLife**|Permite generar perfiles de asignación de memoria mediante el método de muestreo. También permite recopilar datos de duración de objetos.|  
|**SampleLineOff**|Deshabilita la recopilación de datos de generación de perfiles en el nivel de línea. NET.|  
  
 **Opciones de VSPerfCLREnv para la generación de perfiles Global**  
  
 Para generar perfiles de un servicio administrado como una aplicación web ASP.NET que inicia el sistema operativo en lugar del usuario, utilice las opciones de generación de perfiles global de las opciones de VSPerfCLREnv. En la siguiente tabla se describen las versiones globales de las opciones de VSPerfCLREnv. Estas opciones establecen las variables de entorno adecuadas en el registro.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**GlobalTraceOn**|Permite generar perfiles globales mediante el método de instrumentación. No recopila eventos de asignación de memoria ni datos de duración de objetos.|  
|**GlobalTraceGC**|Permite generar perfiles de asignación de memoria globales mediante el método de instrumentación. No permite recopilar datos de duración de objetos.|  
|**GlobalTraceGCLife**|Permite generar perfiles de asignación de memoria globales mediante el método de instrumentación. También permite la recopilación de datos de duración de objetos.|  
|**GlobalSampleOn**|Permite generar perfiles globales mediante el método de muestreo. No permite recopilar eventos de asignación de memoria ni datos de duración de objetos.|  
|**GlobalSampleGC**|Permite generar perfiles de asignación de memoria global mediante el método de muestreo. No permite recopilar datos de duración de objetos.|  
|**GlobalSampleGCLife**|Permite generar perfiles de asignación de memoria global mediante el método de muestreo. También permite recopilar datos de duración de objetos.|  
  
 **Opciones de VSPerfCLREnv para eliminar la configuración de entorno**  
  
 Cuando haya terminado de generar perfiles de la aplicación administrada, utilice una de las siguientes opciones para eliminar las variables de entorno que agregó VSPerfCLREnv. En la siguiente tabla se describe cómo eliminar las variables de entorno estándar y globales:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Off**|Elimina las variables de entorno de generación de perfiles de .NET estándar. Utilice esta opción cuando se hayan utilizado las opciones de VSPerfClrEnv que no sean globales para establecer las variables de entorno del generador de perfiles.|  
|**GlobalOff**|Elimina las variables de entorno de generación de perfiles de .NET global. Utilice esta opción cuando el sistema operativo, y no el generador de perfiles, haya iniciado la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Estas opciones no son necesarias para la generación de perfiles de una aplicación administrada si la aplicación se inicia mediante el explorador de rendimiento en el IDE. El explorador de rendimiento establece toda la configuración de entorno necesaria en su lugar.  
  
 Si no se estableció el entorno correcto durante el proceso de generación de perfiles, se emite una advertencia durante el análisis y los nombres de la función administrada no se resolverán correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)
