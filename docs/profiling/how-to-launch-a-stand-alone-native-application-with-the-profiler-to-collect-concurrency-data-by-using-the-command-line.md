---
title: 'Cómo: Iniciar una aplicación nativa independiente con el generador de perfiles para recopilar datos de simultaneidad utilizando la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 45115b03fe62ecd78815861d6e82f1a0e6b98449
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Cómo: Iniciar una aplicación nativa independiente con el generador de perfiles para recopilar datos de simultaneidad utilizando la línea de comandos
En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar una aplicación independiente nativa (cliente) y recopilar datos de simultaneidad de procesos y de subprocesos.  
  
 Una sesión de generación de perfiles tiene las siguientes partes:  
  
-   Iniciar la aplicación con el generador de perfiles  
  
-   Controlar la recolección de datos  
  
-   Finalizar la sesión de generación de perfiles  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar el generador de perfiles en un símbolo del sistema, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana **Símbolo del sistema** o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="starting-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles  
 Para iniciar una aplicación de destino mediante el generador de perfiles, utilice las opciones **/start** y **/launch** de [VSPerfCmd.exe](../profiling/vsperfcmd.md) para inicializar el generador de perfiles e iniciar la aplicación. Puede especificar **/start** y **/launch** y sus opciones respectivas. También puede agregar la opción **/globaloff** para pausar la recolección de datos en el inicio de la aplicación de destino. Después, use **/globalon** para empezar a recopilar datos.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Para iniciar una aplicación con el generador de perfiles  
  
1.  En un símbolo del sistema, escriba el siguiente comando:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]  
  
     La opción [/output](../profiling/output.md)**:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  
  
     Puede usar cualquiera de las opciones de la tabla siguiente con la opción **/start:concurrency**.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|  
  
2.  Inicie la aplicación de destino escribiendo:  
  
     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`]  
  
     Puede usar cualquiera de las opciones de la tabla siguiente con la opción **/launch**.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/args](../profiling/args.md) **:** `Arguments`|Especifica una cadena que contiene los argumentos de la línea de comandos que se van a pasar a la aplicación de destino.|  
    |[/console](../profiling/console.md)|Inicia la aplicación de línea de comandos de destino en otra ventana.|  
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Especifica la versión de Common Language Runtime (CLR) para generar perfiles si la aplicación carga más de una versión del CLR.|  
  
## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  
  
-   Los pares de opciones de la tabla siguiente inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso que especifica el identificador de proceso (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (*ProcName*). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
-   También puede usar la opción [/mark](../profiling/mark.md) de **VSPerfCmd.exe** para insertar una marca de generación de perfiles en el archivo de datos. El comando **/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario. Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles.  
  
## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Para dejar de recopilar datos de simultaneidad, cierre la aplicación para la que se generan perfiles o invoque la opción **VSPerfCmd /detach**. Después, invoque a la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  
  
#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  
  
1.  Desasocie el generador de perfiles de la aplicación de destino cerrándolo o escribiendo el siguiente comando en un símbolo del sistema:  
  
     **VSPerfCmd /detach**  
  
2.  Apague el generador de perfiles escribiendo el siguiente comando en un símbolo del sistema:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)