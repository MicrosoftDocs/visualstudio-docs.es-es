---
title: Procedimiento Instrumentar un servicio de .NET Framework y recopilar datos de memoria mediante la línea de comandos del generador de perfiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9bc74cbd0d7fbcfec26f4bfe3f334623baf066b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653741"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedimiento Instrumentar un servicio .NET Framework y recopilar datos de memoria mediante el uso de la línea de comandos de Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para instrumentar un servicio de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] y recopilar datos de uso de memoria. Puede recopilar datos de asignación de memoria o recopilar tanto datos de asignación de memoria como de duración de objetos.  

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  No puede generar perfiles de un servicio con el método de instrumentación si el servicio no se puede reiniciar después de iniciar el equipo, como por ejemplo un servicio que se inicia cuando se inicia el sistema operativo.  
>   
>  Las herramientas de línea de comandos de las herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. En equipos de 64 bits, están disponibles versiones de 64 bits y de 32 bits de las herramientas. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-profiling-session"></a>Iniciar la sesión de generación de perfiles  
 Para recopilar datos de rendimiento de un servicio de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas y la herramienta [VSInstr.exe](../profiling/vsinstr.md) para crear una copia instrumentada del archivo binario del servicio.  

 El equipo que hospeda el servicio se debe reiniciar para configurarlo para la generación de perfiles. También debe iniciar el servicio manualmente desde el Administrador de control de servicios. Después, inicie el generador de perfiles y luego el servicio de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  

 Cuando se ejecute el componente instrumentado, los datos de memoria se recopilarán inmediatamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  

 Para finalizar una sesión de generación de perfiles, cierre el servicio y apague explícitamente el generador de perfiles. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>Para iniciar la generación de perfiles de un servicio de .NET Framework  

1. Abra una ventana de símbolo del sistema.  

2. Use la herramienta **VSInstr** para generar una versión instrumentada del archivo binario del servicio.  

3. Use el Administrador de control de servicios para reemplazar el archivo binario original por la versión instrumentada. Asegúrese de que el Tipo de inicio del servicio está establecido en Manual.  

4. Inicialice las variables del entorno de generación de perfiles. Tipo:  

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}  

   -   **/globaltracegc** y **/globaltracegclife** habilitan la recopilación de datos de asignación de memoria y duración de los objetos.  

       |Opción|Descripción|  
       |------------|-----------------|  
       |**/globaltracegc**|Solo recopila datos de asignación de memoria.|  
       |**/globaltracegclife**|Recopila datos de asignación de memoria y de duración de los objetos.|  

5. Reinicie el equipo.  

6. Abra una ventana de símbolo del sistema.  

7. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - La opción **/start: contention** inicializa el generador de perfiles.  

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.  

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para servicios.  

   |                                 Opción                                  |                                                                                                                                                   Descripción                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |               Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.               |
   |              [/crosssession](../profiling/crosssession.md)              | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md)[**:**`Interval`]         |                                                 Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error. Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente. De manera predeterminada, **/start** termina inmediatamente.                                                  |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                             Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **/globaloff** a la línea de comandos **/start**. Utilice **/globalon** para reanudar la generación de perfiles.                                                                              |
   |           [/counter](../profiling/counter.md) **:** `Config`            |                                                                           Recopila información del contador de rendimiento del procesador especificado en Config. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                    Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.                                                                                                                     |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                  Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.                                                                                   |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                     Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.                                                                                     |

8. Si es necesario, inicie el servicio.  

9. Adjunte el generador de perfiles al servicio. Tipo:  

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`  

    -   Especifica el identificador o el nombre de proceso del servicio. Puede ver los nombres e identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  

## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Mientras se ejecuta el servicio, puede controlar la recopilación de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de **VSPerfCmd.exe**. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|  

## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación que está ejecutando el componente instrumentado y, después, inicie la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1.  Detenga el servicio en el Administrador de control de servicios.  

2.  Cierre el generador de perfiles. Tipo:  

     **VSPerfCmd /shutdown**  

3.  Cuando haya finalizado la generación de perfiles, borre las variables de entorno de generación de perfiles. Tipo:  

     **VSPerfClrEnv /globaloff**  

     Reemplace el módulo instrumentado con el original. Si es necesario, vuelva a configurar el Tipo de inicio del servicio.  

4.  Reinicie el equipo.  

## <a name="see-also"></a>Vea también  
 [Generación de perfiles de servicios](../profiling/command-line-profiling-of-services.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)
