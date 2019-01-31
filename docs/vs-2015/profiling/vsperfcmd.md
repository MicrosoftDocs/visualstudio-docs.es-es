---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da82cbd8426b1a9af08e27577cdb76ca4a64d2e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776103"
---
# <a name="vsperfcmd"></a>VSPerfCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta **VSPerfCmd.exe** se usa para iniciar y detener la recopilación de datos de rendimiento. Utiliza la siguiente sintaxis:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 En las tablas siguientes se describen las opciones de la herramienta **VSPerfCmd.exe**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**U**|Se escribe la salida de la consola redirigida como Unicode. Esta debe ser la primera opción especificada.|  
|[Start](../profiling/start.md) **:** `mode`|Inicia el servicio de generación de perfiles en el modo especificado.|  
|[Output](../profiling/output.md) **:** `filename`|Especifica el nombre del archivo de salida. Úselo solo con **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Habilita la generación de perfiles en las sesiones de Windows. Úselo solo con **Start**, **Attach** o **Launch**.|  
|[User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Permite que la cuenta especificada tenga acceso al servicio de generador de perfiles. Úselo solo con **Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Espera a que el registrador de recolección de datos se inicialice. Si se especifica `n`, **VSPerfCmd** esperará a lo sumo `n` segundos. Si no se especifica `n`, **VSPerfCmd** esperará indefinidamente. Esto facilita el uso de **VSPerfCmd** como parte de un proceso por lotes.|  
|[Counter](../profiling/counter.md) **:** `cfg`|Cuando se usa el método de generación de perfiles de muestreo, especifica un contador de CPU y el número de eventos que se usará como intervalo de muestreo. Puede muestrear solo un valor de contador.<br /><br /> Cuando se usa el método de generación de perfiles de instrumentación, especifica un contador de CPU que se recopila en cada punto de instrumentación. Úselo solo con **Start:**`Trace`, **Attach** o **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Muestra una lista de contadores de CPU válidos para la máquina actual.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Especifica un evento de contador de rendimiento de Windows que se incluirá con datos de marca de perfil. Úselo solo con **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Especifica el intervalo de tiempo (en milisegundos) entre los eventos de recopilación de datos de contadores de rendimiento de Windows. Úselo con **WinCounter**.|  
|[Events](../profiling/events-vsperfcmd.md) **:** `option`|Colección de controles de eventos especificados de Seguimiento de eventos para Windows (ETW). Los datos ETW se recopilan en un archivo .itl que no es el archivo de datos de generación de perfiles (.vsp).|  
|[Estado](../profiling/status.md)|Muestra el estado del generador de perfiles, información sobre los procesos de los que se están generando perfiles y las cuentas que tienen autoridad para controlar el generador de perfiles.|  
|[Shutdown](../profiling/shutdown.md)[**:**`n`]|Cierra el archivo de datos de generación de perfiles y desactiva el generador de perfiles.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Reanuda la recopilación de datos después de una llamada a **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Detiene la recopilación de datos, pero no finaliza la sesión de generación de perfiles.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Reanuda la recopilación de datos para el proceso especificado después de que la generación de perfiles se haya pausado mediante una llamada a **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Detiene la recopilación de datos para el proceso especificado.|  
|[ThreadOn y ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Reanuda la generación de perfiles para el proceso especificado después de que esta se haya pausado mediante una llamada a **VSPerfCmdThreadOff**. Use **ThreadOn** solo al generar perfiles con el método de instrumentación.|  
|[ThreadOn y ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Pausa la generación de perfiles para el subproceso especificado. Use **ThreadOff** solo al generar perfiles con el método de instrumentación.|  
|[Mark](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Inserta una marca en el archivo de datos de generación de perfiles, con un texto opcional.|  
  
## <a name="sampling-method-options"></a>Opciones del método de muestreo  
 Las siguientes opciones solo están disponibles cuando se usa el método de generación de perfiles de muestreo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[Launch](../profiling/launch.md) **:** *Ejecutable*|Inicia la aplicación específica y empieza a generar perfiles.|  
|[Args](../profiling/args.md) **:** *Argumentos*|Especifica los argumentos de la línea de comandos que se van a pasar a la aplicación iniciada.|  
|[Consola](../profiling/console.md)|Inicia el comando especificado en una nueva ventana del símbolo del sistema.|  
|[Attach](../profiling/attach.md) **:** *PID*[**,**_PID_]|Inicia la generación de perfiles de los procesos especificados. Los procesos se pueden identificar por identificador de proceso o por nombre de proceso.|  
|[Detach](../profiling/detach.md)[**:**_PID_[,_PID_]]|Detiene la generación de perfiles de los procesos especificados. Los procesos se pueden identificar por identificador de proceso o por nombre de proceso. Si no se especifica ningún proceso, la generación de perfiles se detiene para todos los procesos.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation**`&#124;`**Lifetime**}]|Recopila datos de asignación de memoria de .NET y de duración de los objetos. Úselo solo con la opción **VSPerfCmdLaunch**.|  
  
### <a name="sampling-interval-options"></a>Opciones del intervalo de muestreo  
 Las opciones siguientes especifican el tipo y la duración de los intervalos de muestreo. El valor predeterminado es **Timer**. También puede especificar un contador de CPU como intervalo mediante la opción **Counter**. Estas opciones solo se pueden especificar con **Launch** o con la primera opción **Attach** de una sesión de generación de perfiles.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Muestrea en cada error de página número n (valor predeterminado: 10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Muestrea en cada llamada del sistema número n (valor predeterminado: 10).|  
|[Timer](../profiling/timer.md)[**:**_n_]|Muestrea en cada ciclo del procesador número n (valor predeterminado: 10 000 000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Opciones de componentes de servicios y de dispositivos de modo de núcleo  
 Las siguientes opciones de administración admiten la generación de perfiles de componentes de servicios o controladores de dispositivos de modo de núcleo. Las opciones de administración establecen permisos de generación de perfiles y controlan el servicio o el controlador de dispositivos de los que se han generado perfiles.  
  
 Las opciones de administración deben ejecutarse en un símbolo del sistema que se ejecute con credenciales administrativas.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**> *Right*[ *Right*] \<*User*&#124;*Group*>|Permite o deniega al usuario o grupo especificados el acceso a los servicios de generación de perfiles.<br /><br /> `Right` puede ser:<br /><br /> CrossSession: concede al usuario acceso al servicio para realizar la generación de perfiles entre sesiones.<br /><br /> SampleProfiling: concede al usuario acceso al controlador para habilitar la generación de perfiles de muestreo. También se usa para tener acceso a la información de transición del núcleo durante la generación de perfiles de seguimiento.<br /><br /> FullAccess: concede al usuario acceso de tipo CrossSession y SampleProfiling.|  
|**Admin:Security, List**|Muestra el estado actual de los servicios de generación de perfiles y enumera los permisos de usuario.|  
|**Admin:** \<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Inicia, detiene, instala o desinstala el componente del servicio de generación de perfiles (service) o el controlador de dispositivos de modo de núcleo (driver).|  
|**Admin:** \<*Service*&#124;*Driver*>**AutoStart**\<**ON**&#124;**OFF**>|Habilita o deshabilita el inicio automático del servicio de generación de perfiles (service) o el controlador de dispositivos de modo de núcleo (driver) después de reiniciar.|  
  
## <a name="vsperfcmd-driver"></a>VSPerfCmd /Driver  
 La opción **VSPerfCmd /Driver** ahora está obsoleta. Use la opción **VsPerfCmdAdmin** para esta funcionalidad.  
  
## <a name="see-also"></a>Vea también  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
