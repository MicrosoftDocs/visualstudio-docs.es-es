---
title: 'Cómo: Iniciar una aplicación independiente con el generador de perfiles y recopilar estadísticas de aplicación mediante la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aff0fa2e1bfcc0139b2cb5a2517fe911007df31e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949011"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Cómo: Iniciar una aplicación independiente con el generador de perfiles y recopilar estadísticas de aplicación mediante la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para iniciar una aplicación independiente (cliente) y recopilar estadísticas de rendimiento utilizando el método de muestreo.  

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Consulte [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)  

 Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso a la variable de entorno PATH de la ventana del símbolo del sistema o agregarla al propio comando. Puede ejecutar las herramientas de generación de perfiles en un equipo donde esté instalado Visual Studio desde una ventana de comandos de Visual Studio.  

1.  Si está ejecutando las herramientas de generación de perfiles en un equipo donde esté instalado Visual Studio, una ventana de comandos de Visual Studio establece las rutas de acceso correctas. En el menú **Herramientas**, elija **Símbolo del sistema de VS**  

> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de Visual Studio. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso a la variable de entorno PATH de la ventana del símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles  
 Para iniciar una aplicación de destino con el generador de perfiles, utilice las opciones **/start** y **/launch** de VSPerfCmd para inicializar el generador de perfiles e iniciar la aplicación. Puede especificar **/start** y **/launch** y sus respectivas opciones en una línea de comandos única.  

 También puede agregar la opción **/globaloff** para pausar la recolección de datos en el inicio de la aplicación de destino. Después, use **/globalon** para empezar a recopilar datos.  

#### <a name="to-start-an-application-by-using-the-profiler"></a>Para iniciar una aplicación mediante el generador de perfiles  

1. Abra una ventana de símbolo del sistema.  

2. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  

   - La opción [/start](../profiling/start.md)**:sample** inicializa el generador de perfiles.  

   - La opción [/output](../profiling/output.md)**:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.  

   |                              Opción                              |                                                                  Descripción                                                                  |
   |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` |                                   Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.                                   |
   |      [/automark](../profiling/automark.md) **:** `Interval`      | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   |    [/events](../profiling/events-vsperfcmd.md) **:** `Config`    |   Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.    |


3. Inicie la aplicación de destino. Type:**VSPerfCmd /launch:**`appName` [`Options`] [`Sample Event`]  

    Puede utilizar una o más de las opciones siguientes con la opción **/launch**.  

   |Opción|Descripción|  
   |------------|-----------------|  
   |[/args](../profiling/args.md) **:** `Arguments`|Especifica una cadena que contiene los argumentos de la línea de comandos que se van a pasar a la aplicación de destino.|  
   |[/console](../profiling/console.md)|Inicia la aplicación de línea de comandos de destino en otra ventana.|  

    De manera predeterminada, se realiza un muestreo de los datos de rendimiento cada 10.000.000 ciclos de reloj de procesador no detenidos. Esto equivale aproximadamente a una vez cada 10 segundos en un procesador de 1 GHz. Puede especificar una de las siguientes opciones para cambiar el intervalo del ciclo de reloj o especificar otro evento de muestreo.  

   |Evento de muestreo|Descripción|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|Cambia el intervalo de muestreo por el número de ciclos de reloj no detenidos especificados mediante `Interval`.|  
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Cambia el evento de muestreo a errores de página. Si se especifica `Interval`, se establece el número de errores de página entre un muestreo y otro. El valor predeterminado es 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Cambia el evento de muestreo a llamadas al sistema por parte del proceso al kernel del sistema operativo (llamadas syscall). Si se especifica `Interval`, se establece el número de llamadas entre un muestreo y otro. El valor predeterminado es 10.|  
   |[/counter](../profiling/counter.md) **:** `Config`|Cambia el evento y el intervalo de muestreo por el contador de rendimiento del procesador y el intervalo especificados en `Config`.|  

## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Durante la ejecución de la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de **VSPerfCmd.exe**. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID`  [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por `PID` o por el nombre de proceso (ProcName). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  

## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar adjunto a ningún proceso perfilado y se debe apagar explícitamente. Puede desasociar el generador de perfiles de una aplicación cuyo perfil se ha generado mediante el método de muestreo, el cierre de la aplicación o una llamada la opción **VSPerfCmd /detach**. Después, llame a la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1.  Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:  

    -   Cierre la aplicación de destino.  

         O bien  

    -   Escriba **VSPerfCmd /detach**  

2.  Cierre el generador de perfiles. Tipo:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Vea también  
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)



