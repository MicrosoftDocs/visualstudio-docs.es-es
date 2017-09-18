---
title: "C&#243;mo: Instrumentar un servicio .NET y recopilar datos detallados de control de tiempo utilizando la l&#237;nea de comandos del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Instrumentar un servicio .NET y recopilar datos detallados de control de tiempo utilizando la l&#237;nea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] para instrumentar un servicio de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y recopilar datos de control de tiempo detallados.  
  
> [!NOTE]
>  No puede generar perfiles de un servicio con el método de instrumentación si el servicio no se puede reiniciar después de iniciar el equipo, como por ejemplo un servicio que se inicia solamente cuando se inicia el sistema operativo.  
>   
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles versiones de 64 bits y de 32 bits de las herramientas.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos.  Vea [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Para recopilar datos de control de tiempo detallados de un servicio de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utilizando el método de instrumentación, utilice la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente.  A continuación, reemplace la versión no instrumentada del servicio por la versión instrumentada, asegurándose de que el servicio se configura para iniciarse manualmente.  A continuación, use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno globales de generación de perfiles y, a continuación, reinicie el equipo host.  A continuación, inicie el generador de perfiles.  
  
 Cuando se inicia el servicio, los datos de control de tiempo se recopilan automáticamente en un archivo de datos.  Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  
  
 Para finalizar una sesión de generación de perfiles, desactive el servicio y, a continuación, cierre explícitamente el generador de perfiles.  En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  
  
## Iniciar la aplicación con el generador de perfiles  
  
#### Para iniciar la generación de perfiles de un servicio de .NET Framework  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Utilice la herramienta **VSInstr** para generar una versión instrumentada del archivo binario del servicio.  
  
3.  Reemplace el binario original por la versión instrumentada.  En el Administrador de control de servicios de Windows, asegúrese de que el Tipo de inicio del servicio está establecido en Manual.  
  
4.  Inicialice las variables de entorno de generación de perfiles de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Escriba:  
  
     **VSPerfClrEnv \/globaltraceon**  
  
5.  Reinicie el equipo.  
  
6.  Abra una ventana de símbolo del sistema.  
  
7.  Inicie el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   La opción [\/start](../profiling/start.md)**:trace** inicializa el generador de perfiles.  
  
    -   La opción [\/output](../profiling/output.md)**:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede utilizar cualquiera de las siguientes opciones con la opción **\/start:trace**.  
  
    > [!NOTE]
    >  Las opciones **\/user** y **\/crosssession** son necesarias normalmente para servicios de generación de perfiles.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/usuario](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles.  Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión.  El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otras sesiones.  Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente.  El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows.  **\/CS** se puede especificar como una abreviatura de **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error.  Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente.  De manera predeterminada, **\/start** termina inmediatamente.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **\/globaloff** a la línea de comandos **\/start**.  Utilice **\/globalon** para reanudar la generación de perfiles.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Recopila información del contador de rendimiento del procesador especificado en Config.  La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
  
8.  Inicie el servicio en el Administrador de control de servicios de Windows.  
  
## Controlar la recolección de datos  
 Cuando se está ejecutando el servicio, puede utilizar las opciones de **VSPerfCmd.exe** para iniciar y detener la escritura de datos en el archivo de datos del generador de perfiles.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de un servicio.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso especificado por el identificador de proceso \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) o detiene \(**\/threadoff**\) la recolección de datos del subproceso especificado por el identificador del subproceso \(`TID`\).|  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, detenga el servicio que está ejecutando el componente instrumentado y, a continuación, llame a la opción **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  El comando **VSPerfClrEnv \/globaloff** borra las variables de entorno de generación de perfiles.  
  
 Para que se aplique la configuración de entorno, debe reiniciar el equipo.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Detenga el servicio en el Administrador de control de servicios.  
  
2.  Apague el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Cuando haya finalizado la generación de perfiles, borre las variables de entorno de generación de perfiles.  Escriba:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Reemplace el módulo instrumentado con el original.  Si es necesario, vuelva a configurar el Tipo de inicio del servicio.  
  
5.  Reinicie el equipo.  
  
## Vea también  
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)   
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)