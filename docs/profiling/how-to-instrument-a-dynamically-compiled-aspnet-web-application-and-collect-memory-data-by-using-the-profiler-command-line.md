---
title: "C&#243;mo: Instrumentar una aplicaci&#243;n web ASP.NET compilada din&#225;micamente y recopilar datos de memoria mediante la l&#237;nea de comandos del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Instrumentar una aplicaci&#243;n web ASP.NET compilada din&#225;micamente y recopilar datos de memoria mediante la l&#237;nea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para recopilar datos detallados de asignación de memoria y duración de objetos de .NET de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilada dinámicamente mediante el método de instrumentación de generación de perfiles.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles versiones de 64 bits y de 32 bits de las herramientas.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para recopilar datos de rendimiento de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe modificar el archivo web.config de la aplicación de destino para permitir que la herramienta [VSInstr.exe](../profiling/vsinstr.md) instrumente los archivos de aplicación compilados dinámicamente.  A continuación, utiliza la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para configurar el servidor que hospeda la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y habilita la generación de perfiles de memoria de .NET mediante el establecimiento de las variables de entorno adecuadas y el reinicio del equipo.  
  
 Para recopilar datos, inicie el generador de perfiles y, a continuación, ejecute la aplicación de destino.  Mientras el generador de perfiles esté adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Una vez recopilados los datos adecuados, cierre la aplicación, cierre el proceso de trabajo de Internet Information Services \(IIS\) y, a continuación, apague el generador de perfiles.  
  
 Tras completar el trabajo de generación de perfiles, restaure el estado original del archivo web.config y el servidor web.  
  
## Configurar la aplicación web ASP.NET y el servidor web  
  
#### Para configurar la aplicación web ASP.NET y el servidor web  
  
1.  Modifique el archivo web.config de la aplicación de destino.  Vea [Cómo: Modificar archivos web.config para instrumentar y generar perfiles de aplicaciones web ASP.NET compiladas dinámicamente](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md).  
  
2.  En el equipo que hospeda la aplicación web, abra una ventana del símbolo del sistema.  
  
3.  Inicialice las variables de entorno de generación de perfiles.  Escriba:  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     O bien  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** habilita la recolección de datos de asignación de memoria.  
  
    -   **\/globaltracegclife** habilita la recolección tanto de datos de asignación de memoria como de datos de duración de objetos.  
  
4.  Reinicie el equipo.  
  
## Ejecutar la sesión de generación de perfiles  
  
#### Para generar los perfiles de la aplicación web ASP.NET  
  
1.  Inicie el generador de perfiles.  Escriba:  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   La opción **\/start:trace** inicializa el generador de perfiles.  
  
    -   La opción **\/output:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **\/start:trace**.  
  
    > [!NOTE]
    >  Las opciones **\/user** y **\/crosssession** son necesarias normalmente para aplicaciones ASP.NET.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/usuario](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica el dominio y el nombre de usuario opcionales de la cuenta propietaria del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión.  El nombre se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otras sesiones.  Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente.  El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows.  **\/CS** se puede especificar como una abreviatura de **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Inicia el generador de perfiles con la recolección de datos en pausa.  Utilice [\/globalon](../profiling/globalon-and-globaloff.md) para reanudar la generación de perfiles.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Recopila información del contador de rendimiento del procesador especificado en `Config`.  La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
  
2.  Inicie la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de la manera habitual.  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de **VSPerfCmd.exe**.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso especificado por el identificador de proceso \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) o detiene \(**\/threadoff**\) la recolección de datos del subproceso especificado por el identificador del subproceso \(`TID`\).|  
  
-   También puede usar la opción **VSPerfCmd.exe**[\/mark](../profiling/mark.md) para insertar una marca de generación de perfiles en el archivo de datos.  El comando **\/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario.  Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles.  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de destino, detenga Internet Information Services \(IIS\) para detener el proceso perfilado y, a continuación, apague el generador de perfiles.  A continuación, reinicie IIS.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] restableciendo Internet Information Services \(IIS\).  Escriba:  
  
     **IISReset \/stop**  
  
3.  Apague el generador de perfiles.  Escriba:  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  Reinicie IIS.  Escriba:  
  
     **IISReset \/start**  
  
## Restaurar la configuración del equipo y la aplicación  
 Después de completar la generación de perfiles, reemplace el archivo web.config, borre las variables de entorno de generación de perfiles y reinicie el equipo para restaurar el servidor y la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a sus estados originales.  
  
#### Para restaurar la configuración del equipo y la aplicación  
  
1.  Reemplace el archivo web.config con una copia del archivo original.  
  
2.  \(Opcional\).  Borre las variables del entorno de generación de perfiles.  Escriba:  
  
     **VSPerfCmd \/globaloff**  
  
3.  Reinicie el equipo.  
  
## Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)