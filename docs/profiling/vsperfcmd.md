---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "línea de comandos, herramientas"
  - "herramientas de la línea de comandos, VSPerfCmd (herramienta)"
  - "herramientas de rendimiento, VSPerfCmd (herramienta)"
  - "herramientas de generación de perfiles, VSPerfCmd"
  - "VSPerfCmd (herramienta)"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La herramienta **VSPerfCmd.exe** se utiliza para iniciar y detener la recolección de datos de rendimiento.  Utiliza la sintaxis siguiente:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 Las tablas siguientes describen las opciones de la herramienta **VSPerfCmd.exe**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**U**|La salida de la consola redirigida se escribe como Unicode.  Debe ser la primera opción especificada.|  
|[Iniciar](../profiling/start.md) **:** `mode`|Inicia el servicio de generación de perfiles en el modo especificado.|  
|[Salida](../profiling/output.md) **:** `filename`|Especifica el nombre del archivo de salida.  Se utiliza únicamente con **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Permite la generación de perfiles en las sesiones de Windows.  Se utiliza únicamente con **Start**, **Attach**, **or Launch**.|  
|[Usuario](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Permite el acceso de la cuenta especificada al servicio del generador de perfiles.  Se utiliza únicamente con **Start**.|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|Espera a que se inicialice el registrador de recolección de datos.  Si se especifica `n`, **VSPerfCmd** esperará a lo sumo `n` segundos.  Si no se especifica `n`, **VSPerfCmd** esperará indefinidamente.  De este modo se facilita el uso de **VSPerfCmd** como parte de un proceso por lotes.|  
|[Contador](../profiling/counter.md) **:** `cfg`|Cuando se utiliza el método de generación de perfiles de muestreo, especifica un contador de CPU y el número de eventos que se va a utilizar como intervalo del muestreo.  Puede probar solamente un valor del contador.<br /><br /> Cuando se utiliza el método de generación de perfiles de instrumentación, especifica un contador de CPU que se va a recopilar en cada punto de instrumentación.  Se utiliza únicamente con **Start:**`Trace`, **Attach**  o **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Muestra una lista de contadores de CPU válidos para el equipo actual.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Especifica un evento de contador de rendimiento de Windows para incluirlo con datos de marca de perfil.  Se utiliza únicamente con **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Especifica el intervalo de tiempo \(en milisegundos\) entre eventos de recolección de datos de contador de rendimiento de Windows.  Se utiliza con **WinCounter**.|  
|[Eventos](../profiling/events-vsperfcmd.md) **:** `option`|Controla la recolección de eventos especificados de la traza de eventos para Windows \(ETW\).  Los datos de ETW se recopilan en un archivo .itl que no es el archivo de datos de generación de perfiles \(.vsp\).|  
|[Estado](../profiling/status.md)|Muestra el estado del generador de perfiles, información sobre los procesos para los que se están generando perfiles actualmente, y las cuentas que tienen autoridad para controlar el generador de perfiles.|  
|[Apagar](../profiling/shutdown.md)\[**:**`n`\]|Cierra el archivo de datos de generación de perfiles y desactiva el generador de perfiles.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Reanuda la recolección de datos después de una llamada a **VSPerfCmd GlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Detiene toda la recolección de datos, pero no finaliza la sesión de generación de perfiles.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Reanuda la recolección de datos para el proceso especificado después de que una llamada a **VSPerfCmdProcessOff** haya puesto en pausa la generación de perfiles.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Detiene la recolección de datos para el proceso especificado.|  
|[ThreadOn y ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Reanuda la generación de perfiles para el proceso especificado después de que una llamada a **VSPerfCmd ThreadOff** haya puesto en pausa la generación de perfiles.  Use **ThreadOn** sólo en la generación de perfiles con el método de instrumentación.|  
|[ThreadOn y ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Pone en pausa la generación de perfiles para el subproceso especificado.  Use **ThreadOff** sólo en la generación de perfiles con el método de instrumentación.|  
|[Marca](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|Inserta una marca en el archivo de datos de generación de perfiles, con texto opcional.|  
  
## Opciones del método de muestreo  
 Las opciones siguientes solo están disponibles cuando se utiliza el método de generación de perfiles de muestreo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[Iniciar](../profiling/launch.md) **:** *Executable*|Inicia la aplicación especificada y la generación de perfiles.|  
|[Args](../profiling/args.md) **:** *Arguments*|Especifica los argumentos de línea de comandos que se van a pasar a la aplicación iniciada.|  
|[Consola](../profiling/console.md)|Inicia el comando especificado en una nueva ventana de símbolo del sistema.|  
|[Asociar](../profiling/attach.md) **:** *PID*\[**,***PID*\]|Inicia la generación de perfiles de los procesos especificados.  Los procesos se pueden identificar por el identificador de proceso o por el nombre de proceso.|  
|[Desasociar](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|Detiene la generación de perfiles de los procesos especificados.  Los procesos se pueden identificar por el identificador de proceso o por el nombre de proceso.  Si no se especifica ningún proceso, el generador de perfiles se detiene para todos los procesos.|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation**}\]                 `&#124;` **Lifetime**}\]|Recopila datos referentes a la duración de objetos y la asignación de memoria de .NET.  Se utiliza únicamente con la opción **Launch** de **VSPerfCmd**.|  
  
### Opciones del intervalo de muestreo  
 Las opciones siguientes especifican el tipo y la duración de los intervalos de muestreo.  El valor predeterminado es **Timer**.  También se puede especificar un contador de CPU como intervalo utilizando la opción **Counter**.  Estas opciones solo se pueden especificar con **Launch** o con la primera asociación \(**Attach**\) de una sesión de generación de perfiles.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[PF](../profiling/pf.md)\[**:***n*\]|Toma una muestra en cada enésimo error de página \(valor predeterminado\=10\).|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|Toma una muestra en cada enésima llamada del sistema \(valor predeterminado\=10\).|  
|[Timer](../profiling/timer.md)\[**:***n*\]|Toma una muestra en cada enésimo ciclo de procesador \(valor predeterminado \= 10000000\).|  
  
## Opciones de componentes del servicio y dispositivos de modo kernel  
 Las opciones Admin siguientes admiten componentes del servicio de generación de perfiles o controladores de dispositivos de modo kernel.  Las opciones Admin establecen los permisos para la generación de perfiles y controlan el servicio para el que se generan perfiles o el controlador de dispositivos.  
  
 Las opciones Admin deben ejecutarse en un símbolo del sistema que se esté ejecutando con credenciales administrativas.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|Permite o deniega al usuario o grupo especificado el acceso a los servicios de generación de perfiles.<br /><br /> `Right` puede ser:<br /><br /> CrossSession: proporciona al usuario acceso al servicio para la generación de perfiles entre sesiones.<br /><br /> SampleProfiling: concede al usuario acceso al controlador para habilitar la generación de perfiles de ejemplo.  También se utiliza para tener acceso a la información de transición del kernel durante la generación de perfiles de traza.<br /><br /> FullAccess: concede al usuario acceso tanto de tipo CrossSession como de tipo SampleProfiling.|  
|**Admin:Security, List**|Muestra el estado actual de los servicios de generación de perfiles y enumera los permisos de usuario.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|Inicia, detiene, instala o desinstala el componente del servicio de generación de perfiles \(servicio\) o el controlador de dispositivos de modo kernel \(controlador\).|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|Habilita o deshabilita automáticamente el inicio del servicio de generación de perfiles \(servicio\) o el controlador de dispositivos de modo kernel \(controlador\) después de un reinicio.|  
  
## VSPerfCmd \/Driver  
 La opción **VSPerfCmd \/Driver** ya está obsoleta.  Utilice las opciones **Admin** de **VsPerfCmd** para esta funcionalidad.  
  
## Vea también  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)