---
title: "C&#243;mo: Adjuntar el generador de perfiles a una aplicaci&#243;n web ASP.NET para recopilar datos de memoria mediante la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Adjuntar el generador de perfiles a una aplicaci&#243;n web ASP.NET para recopilar datos de memoria mediante la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de la línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y recopilar datos sobre el número y tamaño de asignaciones de memoria de .NET Framework.  También puede recopilar datos sobre la duración de los objetos de memoria de .NET Framework.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para recopilar datos de rendimiento de una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe usar la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas en el equipo que hospeda la aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  A continuación, debe reiniciar el equipo para configurar el servidor web para la generación de perfiles.  
  
 A continuación, utilice la herramienta [VSPerfCmd.exe](../profiling/vsperfcmd.md) para adjuntar el generador de perfiles al proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que hospeda el sitio web.  Cuando el generador de perfiles se adjunta a la aplicación, puede pausar y reanudar la recolección de datos.  
  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto a la aplicación y debe cerrarse explícitamente.  En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  
  
## Adjuntar el generador de perfiles  
  
#### Para adjuntar el generador de perfiles a una aplicación web ASP.NET  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Inicialice las variables de entorno de generación de perfiles.  Escriba:  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   Opciones **\/globalsamplegc** y **\/globalsamplegclife** especifican el tipo de datos de memoria a recopilar.  
  
         Especifique una y solamente una de las siguientes opciones.  
  
        |Opción|Descripción|  
        |------------|-----------------|  
        |**\/globalsamplegc**|Habilita la recopilación de datos de asignación de memoria.|  
        |**\/globalsamplegclife**|Habilita la recopilación tanto de datos de asignación de memoria como de datos de duración de objetos.|  
  
    -   La opción **\/samplelineoff** deshabilita la asignación de los datos recopilados a líneas de código fuente específicas.  Si se especifica esta opción, los datos se asignan al nivel de función.  
  
3.  Reinicie el equipo para establecer la nueva configuración de entorno.  
  
4.  Abra una ventana de símbolo del sistema.  Si es necesario, establezca la variable de entorno de ruta de acceso del generador de perfiles.  
  
5.  Inicie el generador de perfiles.  Escriba:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   La opción **\/start:sample** inicializa el generador de perfiles.  
  
    -   La opción **\/output:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **\/start:sample**.  
  
    > [!NOTE]
    >  Las opciones **\/user** y **\/crosssession** son necesarias normalmente para aplicaciones ASP.NET.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/usuario](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET.  Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión.  El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.  Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión.  El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows.  **\/CS** se puede especificar como una abreviatura de **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error.  Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente.  De manera predeterminada, **\/start** termina inmediatamente.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
  
6.  Inicie la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de la manera habitual.  
  
7.  Adjunte el generador de perfiles al proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Escriba:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   El identificador `(PID)` especifica el identificador de proceso o el nombre del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  
  
    -   **\/targetclr:** `Version` especifica la versión de Common Language Runtime \(CLR\) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de **VSPerfCmd.exe**.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso especificado por `PID`.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|**\/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso o por el nombre de proceso.  **\/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de la aplicación web.  Puede detener la recolección de datos de una aplicación para la que se ha realizado la generación de perfiles con el método de muestreo reiniciando el proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o llamando a la opción **VSPerfCmd \/detach**.  A continuación, llame a la opción **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  El comando **VSPerfClrEnv \/globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece una vez reiniciado el equipo.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:  
  
    -   Escriba **VSPerfCmd** [\/detach](../profiling/detach.md)  
  
         O bien  
  
    -   Cierre el proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Escriba:  
  
     **IISReset \/stop**  
  
2.  Apague el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Opcional\) Borre las variables del entorno de generación de perfiles.  Escriba:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Reinicie el equipo.  Si es necesario, reinicie Internet Information Services \(IIS\).  Escriba:  
  
     **IISReset \/start**  
  
## Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)