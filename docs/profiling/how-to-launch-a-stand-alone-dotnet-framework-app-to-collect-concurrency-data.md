---
title: Procedimiento para iniciar una aplicación independiente de .NET Framework con Profiler para recopilar datos de simultaneidad mediante la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5cece8a5b97f3a9c78bdda8c5e841661d2b4d58d
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335585"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Cómo: Iniciar una aplicación de .NET Framework independiente con el generador de perfiles para recopilar datos de simultaneidad utilizando la línea de comandos
En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar una aplicación independiente (cliente) de .NET Framework y recopilar datos de simultaneidad de procesos y de subprocesos.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. En equipos de 64 bits, están disponibles versiones de 64 bits y de 32 bits de las herramientas. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando. Para más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya asociado a la aplicación y debe cerrarse explícitamente.  
  
## <a name="start-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles  
 Para iniciar una aplicación de destino de .NET Framework con el generador de perfiles, utilice VSPerfClrEnv.exe para establecer las variables de generación de perfiles de .NET Framework. Luego, use las opciones **/start** y **/launch** de VSPerfCmd para inicializar Profiler e iniciar la aplicación. Puede especificar **/start** y **/launch** y sus respectivas opciones en una línea de comandos única. También puede agregar la opción **/globaloff** a la línea de comandos para pausar la recolección de datos cuando se inicia la aplicación de destino. A continuación, use **/globalon** en una línea de comandos independiente para empezar a recopilar datos.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Para iniciar una aplicación con el generador de perfiles  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Inicie el generador de perfiles. Tipo:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:**`OutputFile` [`Options`]  
  
    -   La opción [/start](../profiling/start.md) inicializa Profiler.  
  
        |||  
        |-|-|  
        |**/start:concurrency**|Habilita la recolección tanto de datos de contención de recursos como de ejecución de subprocesos.|  
        |**/start:concurrency,resourceonly**|Habilita únicamente la recolección de datos de contención de recursos.|  
        |**/start:concurrency,threadonly**|Habilita únicamente la recolección de datos de ejecución de subprocesos.|  
  
    -   La opción [/output](../profiling/output.md)**:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **/start:concurrency**.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Especifica el dominio y el nombre de usuario opcionales de la cuenta a la que se va a conceder acceso al generador de perfiles.|  
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|  
  
3.  Inicie la aplicación de destino. Tipo:  
  
     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]  
  
     Puede usar cualquiera de las siguientes opciones con la opción **/launch**.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/args](../profiling/args.md) **:** `Arguments`|Especifica una cadena que contiene los argumentos de la línea de comandos que se van a pasar a la aplicación de destino.|  
    |[/console](../profiling/console.md)|Inicia la aplicación de línea de comandos de destino en otra ventana.|  
    |[/targetclr](../profiling/targetclr.md) **:** `Version`|Especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.|  
  
## <a name="control-data-collection"></a>Control de la recopilación de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de la aplicación.  
  
#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  
  
1.  Los siguientes pares de opciones de VSPerfCmd.exe inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inicia la recopilación de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (ProcName). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Para dejar de recopilar datos de simultaneidad, cierre la aplicación para la que se generan perfiles o invoque la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.  
  
#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  
  
1.  Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino.  
  
    -   Cierre la aplicación de destino.  
  
         O bien  
  
    -   Escriba **VSPerfCmd /detach**  
  
2.  Apague el generador de perfiles.  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Vea también  
 [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)