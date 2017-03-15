---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de línea de comandos, VSPerfCLREnv"
  - "línea de comandos, herramientas"
  - "herramientas de rendimiento, VSPerfCLREnv"
  - "herramientas de generación de perfiles, VSPerfCLREnv"
  - "VSPerfCLREnv (herramienta)"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La herramienta VSPerfCLREnv se utiliza para establecer las variables de entorno necesarias para generar perfiles de una aplicación.NET Framework.  Utiliza la sintaxis siguiente:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 La opción que elija dependerá de cuál de los tres tipos de generación de perfiles va a utilizar: muestreo, instrumentación o global.  Se necesita una opción independiente que incluya los datos de interacción de nivel en la generación de perfiles.  La sintaxis para cada opción se describe en las tablas siguientes.  
  
> [!NOTE]
>  Cuando termine de generar los perfiles, ejecute **VSPerfCLREnv** con la opción **\/off** o **\/globaloff** para eliminar las variables de entorno necesarias para la generación de perfiles.  Para obtener más información, vea Opciones de VSPerfCLREnv para eliminar la configuración del entorno, que se incluye más adelante.  
  
 **Opciones de VSPerfCLREnv para incluir datos de interacción de capas**  
  
> [!WARNING]
>  La generación de perfiles de interacción de capas se puede recopilar usando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] y [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 La generación de perfiles de interacción de capas proporciona información adicional sobre las consultas de ADO.NET en aplicaciones de varios niveles.  Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  Los datos de interacción se pueden agregar a cualquier generación de perfiles utilizando cualquier método de generación de perfiles.  
  
 Las opciones **InteractionOn** y **GlobalInteractionOn** habilitan la recopilación de datos de interacción de capas.  La opción de interacción debe establecerse después del establecimiento de la variable de entorno VSPerfCLREnv que se requiere para generar perfiles de una aplicación.  
  
 En el ejemplo siguiente se incluyen datos de interacción de capas en una generación de perfiles que utiliza el método de muestreo:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 En el ejemplo siguiente se incluyen datos de interacción de capas en una generación de perfiles que se ejecuta para un servicio de Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Opciones de VSPerfCLREnv para la generación de perfiles de instrumentación de procesos**  
  
 En la tabla siguiente se describen las opciones de VSPerfCLREnv para la generación de perfiles de instrumentación:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**TraceOn**|Habilita la generación de perfiles mediante el método de instrumentación.  No habilita la generación de perfiles de asignación de memoria ni la recolección de datos de duración de los objetos.|  
|**TraceGC**|Habilita la generación de perfiles de asignación de memoria mediante el método de instrumentación.  No habilita la recolección de datos de duración de los objetos.|  
|**TraceGCLife**|Habilita la generación de perfiles de asignación de memoria y la recopilación de datos de duración de objetos mediante el método de instrumentación.|  
  
 **Opciones de VSPerfCLREnv para la generación de perfiles de muestreo de procesos**  
  
 En la tabla siguiente se describen las opciones de VSPerfCLREnv para la generación de perfiles de muestreo:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**SampleOn**|Habilita la generación de perfiles mediante el método de muestreo.  No habilita la generación de perfiles de asignación de memoria ni la recolección de datos de duración de los objetos.|  
|**SampleGC**|Habilita la generación de perfiles de asignación de memoria mediante el método de muestreo.  No habilita la recolección de datos de duración de los objetos.|  
|**SampleGCLife**|Habilita la generación de perfiles de asignación de memoria mediante el método de muestreo.  También habilita la recolección de datos de duración de los objetos.|  
|**SampleLineOff**|Deshabilita la recolección de datos de generación de perfiles de nivel de línea de .NET.|  
  
 **Opciones de VSPerfCLREnv para la generación de perfiles global**  
  
 Para generar perfiles de un servicio administrado como una aplicación web ASP.NET que es iniciada por el sistema operativo en lugar de por el usuario, utilice las opciones de VSPerfCLREnv para la generación de perfiles global.  En la tabla siguiente se describen las versiones globales de opciones de VSPerfCLREnv.  Estas opciones establecen las variable de entorno adecuadas en el Registro.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**GlobalTraceOn**|Habilita la generación de perfiles global mediante el método de instrumentación.  No recopila eventos de asignación de memoria ni datos de duración de los objetos.|  
|**GlobalTraceGC**|Habilita la generación de perfiles de asignación de memoria global mediante el método de instrumentación.  No habilita la recolección de datos de duración de los objetos.|  
|**GlobalTraceGCLife**|Habilita la generación de perfiles de asignación de memoria global mediante el método de instrumentación.  También habilita la recolección de datos de duración de los objetos.|  
|**GlobalSampleOn**|Habilita la generación de perfiles global mediante el método de muestreo.  No habilita la recolección de eventos de asignación de memoria ni de datos de duración de los objetos.|  
|**GlobalSampleGC**|Habilita la generación de perfiles de asignación de memoria global mediante el método de muestreo.  No habilita la recolección de datos de duración de los objetos.|  
|**GlobalSampleGCLife**|Habilita la generación de perfiles de asignación de memoria global mediante el método de muestreo.  También habilita la recolección de datos de duración de los objetos.|  
  
 **Opciones de VSPerfCLREnv para eliminar la configuración del entorno**  
  
 Una vez terminada la generación de perfiles de la aplicación administrada, utilice una de las opciones siguientes para eliminar las variables de entorno agregadas por VSPerfCLREnv.  En la tabla siguiente se describe cómo eliminar las variables de entorno estándar y globales:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Off**|Elimina las variables de entorno para la generación de perfiles de .NET estándar.  Utilice esta opción cuando las opciones de VSPerfClrEnv no globales se utilizaron para establecer las variables de entorno del generador de perfiles.|  
|**GlobalOff**|Elimina las variables de entorno para la generación de perfiles globales de .NET.  Utilice esta opción si la aplicación la inició el sistema operativo y no el generador de perfiles.|  
  
## Comentarios  
 Estas opciones no se requieren para la generación de perfiles de una aplicación administrada si la aplicación se inicia mediante el Explorador de rendimiento en el IDE.  El Explorador de rendimiento establece toda la configuración de entorno necesaria.  
  
 Si no se estableció el entorno correcto durante la generación de perfiles, se muestra una advertencia durante el análisis y los nombres de las funciones administradas no se resolverán correctamente.  
  
## Vea también  
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)