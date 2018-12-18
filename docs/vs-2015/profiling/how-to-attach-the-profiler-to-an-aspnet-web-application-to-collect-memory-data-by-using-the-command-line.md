---
title: 'Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar datos de memoria mediante la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6818c7c23a1ca42fc4537e1024778cd4cab0f177
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794587"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar datos de memoria mediante la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de la línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para adjuntar el generador de perfiles a una aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] y recopilar datos sobre el número y tamaño de asignaciones de memoria de .NET Framework. También puede recopilar datos sobre la duración de los objetos de memoria de .NET Framework.  

> [!NOTE]
>  Las herramientas de línea de comandos de las herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Para recopilar datos de rendimiento de una aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], debe usar la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas en el equipo que hospeda la aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. A continuación, debe reiniciar el equipo para configurar el servidor web para la generación de perfiles.  

 Después, se usa la herramienta [VSPerfCmd.exe](../profiling/vsperfcmd.md) para adjuntar el generador de perfiles al proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que hospeda el sitio web. Cuando el generador de perfiles se adjunta a la aplicación, puede pausar y reanudar la recolección de datos.  

 Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto a la aplicación y debe cerrarse explícitamente. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  

## <a name="attaching-the-profiler"></a>Adjuntar el generador de perfiles  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Para adjuntar el generador de perfiles a una aplicación web ASP.NET  

1. Abra una ventana de símbolo del sistema.  

2. Inicialice las variables del entorno de generación de perfiles. Tipo:  

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  

   -   Las opciones **/globalsamplegc** y **/globalsamplegclife** especifican el tipo de datos de memoria que se van a recopilar.  

        Especifique una y solamente una de las siguientes opciones.  

       |Opción|Descripción|  
       |------------|-----------------|  
       |**/globalsamplegc**|Habilita la recopilación de datos de asignación de memoria.|  
       |**/globalsamplegclife**|Habilita la recopilación tanto de datos de asignación de memoria como de datos de duración de objetos.|  

   -   La opción **/samplelineoff** desactiva la asignación de los datos recopilados a líneas de código fuente específicas. Si se especifica esta opción, los datos se asignan al nivel de función.  

3. Reinicie el equipo para establecer la nueva configuración de entorno.  

4. Abra una ventana de símbolo del sistema. Si es necesario, establezca la variable de entorno de ruta de acceso del generador de perfiles.  

5. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - La opción **/start:sample** inicializa el generador de perfiles.  

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.  

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.  

   |                                 Opción                                  |                                                                                                                                                        Descripción                                                                                                                                                        |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                   Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.                    |
   |              [/crosssession](../profiling/crosssession.md)              | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md) [**:**`Interval`]        |                                                      Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error. Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente. De manera predeterminada, **/start** termina inmediatamente.                                                      |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                         Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                       Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.                                                                                       |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.                                                                                          |


6. Inicie la aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de la manera habitual.  

7. Adjunte el generador de perfiles al proceso de trabajo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Tipo:  

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   -   El Id. de proceso `(PID)` especifica el identificador de proceso o el nombre del proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  

   -   **/targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.  

## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Durante la ejecución de la aplicación, puede controlar la recopilación de datos iniciando o deteniendo la escritura de los datos en el archivo de datos del generador de perfiles mediante el uso de las opciones de **VSPerfCmd.exe**. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recopilación de datos para el proceso especificado por el `PID`.|  
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/attach** inicia la recopilación de datos para el proceso especificado por el identificador o nombre de proceso. **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  

## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de la aplicación web. Puede detener la recopilación de datos de una aplicación para la que se ha realizado la generación de perfiles con el método de muestreo reiniciando el proceso de trabajo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o llamando a la opción **VSPerfCmd /detach**. Después, llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1. Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:  

   - Escriba **VSPerfCmd** [/detach](../profiling/detach.md)  

      O bien  

   - Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Tipo:  

     **IISReset /stop**  

2. Cierre el generador de perfiles. Tipo:  

    **VSPerfCmd /shutdown**  

3. (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:  

    **VSPerfCmd /globaloff**  

4. Reinicie el equipo. Si es necesario, reinicie Internet Information Services (IIS). Tipo:  

    **IISReset /start**  

## <a name="see-also"></a>Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)



