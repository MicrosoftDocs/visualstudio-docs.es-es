---
title: Asociación del generador de perfiles a la aplicación web ASP.NET para obtener estadísticas de aplicación
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 4ff01635e754f2f615247e998aad765c1b366e69
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261423"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Procedimiento para adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar estadísticas de aplicación mediante la línea de comandos
En este artículo se describe cómo usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a una aplicación web ASP.NET y recopilar estadísticas de rendimiento con el método de muestreo.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

 Si desea recopilar datos de rendimiento de una aplicación web ASP.NET, debe inicializar las variables de entorno adecuadas y reiniciar el equipo que hospeda la aplicación web ASP.NET para configurar el servidor web para la generación de perfiles.

 A continuación, debe adjuntar el generador de perfiles al proceso de trabajo de ASP.NET que hospeda el sitio web. Cuando el generador de perfiles se adjunta a la aplicación, puede pausar y reanudar la recolección de datos.

 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de la aplicación para la que se generan perfiles y se debe apagar explícitamente. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Iniciar el generador de perfiles y adjuntarlo a una aplicación web ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Para adjuntar el generador de perfiles a una aplicación web ASP.NET

1. Abra una ventana de símbolo del sistema.

2. Inicialice las variables del entorno de generación de perfiles. Tipo:

    **VSPerfClrEnv /globalsampleon** [ **/samplelineoff**]

   - **/globalsampleon** habilita el muestreo.

   - **/samplelineoff** desactiva la asignación de los datos recopilados a líneas de código fuente específicas. Cuando se especifica esta opción, los datos se asignan solo a funciones.

3. Reinicie el equipo.

4. Inicie el generador de perfiles. Escriba:**VSPerfCmd** [/start](../profiling/start.md) **:sample** [/output](../profiling/output.md) **:** `OutputFile`[`Options`]

   - La opción **/start:sample** inicializa el generador de perfiles.

   - La opción **/output:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar cualquiera de las opciones siguientes con la opción **/start:sample**.

   > [!NOTE]
   > Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente. |

5. Inicie la aplicación web ASP.NET de la manera habitual.

6. Adjunte el generador de perfiles al proceso de trabajo de ASP.NET. Escriba:**VSPerfCmd** [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:** `Version`]

   - `PID` especifica el identificador del proceso de trabajo de ASP.NET; `ProcName` especifica el nombre del proceso de trabajo. Puede ver los nombres e identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

   - De manera predeterminada, se realiza un muestreo de los datos de rendimiento cada 10.000.000 ciclos de reloj de procesador no detenidos. En un procesador de 1 GH, equivale aproximadamente a 100 veces por segundo. Puede especificar una de las opciones de **VSPerfCmd** siguientes para cambiar el intervalo de ciclos de reloj o especificar otro evento de muestreo.

   |Evento de muestreo|Descripción|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|Cambia el intervalo de muestreo por el número de ciclos de reloj no detenidos especificados mediante `Interval`.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|Cambia el evento de muestreo a errores de página. Si se especifica `Interval`, se establece el número de errores de página entre un muestreo y otro. El valor predeterminado es 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Cambia el evento de muestreo a llamadas al sistema por parte del proceso al kernel del sistema operativo (llamadas syscall). Si se especifica `Interval`, se establece el número de llamadas entre un muestreo y otro. El valor predeterminado es 10.|
   |[/counter](../profiling/counter.md) **:** `Config`|Cambia el evento y el intervalo de muestreo por el contador de rendimiento del procesador y el intervalo especificados en `Config`.|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.|

   - **targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Cuando se ejecuta la aplicación, puede controlar la recopilación de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recopilación de datos para el proceso especificado por `PID`.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por `PID` o por el nombre de proceso (ProcName). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y use el comando **IISReset** de Internet Information Services (IIS) para cerrar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.

 El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles. Para que se aplique la configuración de entorno, debe reiniciar el equipo.

 El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino:

   - Escriba **VSPerfCmd /detach**

      o bien

   - Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Cierre el generador de perfiles. Escriba:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:

    **VSPerfCmd /globaloff**

4. Reinicie el equipo.

## <a name="see-also"></a>Vea también
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)