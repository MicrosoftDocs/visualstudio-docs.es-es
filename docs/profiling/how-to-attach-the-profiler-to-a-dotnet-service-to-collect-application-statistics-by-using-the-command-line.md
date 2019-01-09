---
title: Asociación del generador de perfiles a un servicio de .NET para recopilar estadísticas de la aplicación
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 22d84b09751017aa7d92bcda1e5910736876bb66
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592955"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Procedimiento Asociar el generador de perfiles a un servicio .NET para recopilar estadísticas de aplicación mediante la línea de comandos
En este artículo se describe cómo usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a un servicio de .NET Framework y recopilar estadísticas de rendimiento con el método de muestreo.  

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.  
> 
>  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Para recopilar datos de rendimiento de un servicio de .NET Framework, debe usar la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas. A continuación, debe reiniciar el equipo que hospeda el servicio y configurarlo para la generación de perfiles. Después debe adjuntar el generador de perfiles al proceso del servicio. Mientras el generador de perfiles está adjunto al servicio, puede pausar y reanudar la recolección de datos.  

 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar del servicio y se debe cerrar explícitamente. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  

## <a name="attach-the-profiler"></a>Anexión del generador de perfiles  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Para adjuntar el generador de perfiles a un servicio de .NET Framework  

1. Instale el servicio.  

2. Abra una ventana de símbolo del sistema.  

3. Inicialice las variables del entorno de generación de perfiles. Tipo:  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   -   **/globalsampleon** habilita el muestreo.  

   -   **/samplelineoff** desactiva la asignación de los datos recopilados a líneas de código fuente específicas. Cuando se especifica esta opción, los datos se asignan solo a funciones.  

4. Reinicie el equipo.  

5. Abra una ventana de símbolo del sistema.  

6. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - La opción **/start:sample** inicializa el generador de perfiles.  

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.  

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para servicios.  

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si el servicio se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente. |


7. Si es necesario, inicie el servicio.  

8. Adjunte el generador de perfiles al servicio. Tipo:  

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Especifique el identificador de proceso (`PID`) o nombre de proceso (ProcName) del servicio. Puede ver los nombres e identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  

     De manera predeterminada, se realiza un muestreo de los datos de rendimiento cada 10.000.000 ciclos de reloj de procesador no detenidos. En un procesador de 1 GH, equivale aproximadamente a 100 muestras por segundo. Puede especificar una de las siguientes opciones para cambiar el intervalo del ciclo de reloj o especificar otro evento de muestreo.  

   |Evento de muestreo|Descripción|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|Cambia el intervalo de muestreo al número de ciclos de reloj no detenidos especificado en `Interval`.|  
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Cambia el evento de muestreo a errores de página. Si se especifica `Interval`, se establece el número de errores de página entre un muestreo y otro. El valor predeterminado es 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Cambia el evento de muestreo a llamadas al sistema por parte del proceso al kernel del sistema operativo (llamadas syscall). Si se especifica `Interval`, se establece el número de llamadas entre un muestreo y otro. El valor predeterminado es 10.|  
   |[/counter](../profiling/counter.md) **:** `Config`|Cambia el evento y el intervalo de muestreo al contador de rendimiento del procesador y al intervalo especificados en `Config`.|  

   -   **targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.  

## <a name="control-data-collection"></a>Controlar la recopilación de datos  
 Cuando se está ejecutando el servicio, puede usar las opciones de *VSPerfCmd.exe* para iniciar y detener la escritura de datos en el archivo de datos del generador de perfiles. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso o por el nombre de proceso. **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente. Puede desasociar el generador de perfiles de una aplicación para la que se generan perfiles con el método de muestreo cerrando la aplicación o llamando a la opción **VSPerfCmd /detach**. Después, llame a la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  

 El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1.  Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino:  

    -   Detenga el servicio.  

         O bien  

    -   Escriba **VSPerfCmd /detach**  

2.  Cierre el generador de perfiles. Tipo:  

     **VSPerfCmd /shutdown**  

3.  (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:  

     **VSPerfClrEnv /globaloff**  

4.  Reinicie el equipo.  

## <a name="see-also"></a>Vea también  
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)   
 [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)