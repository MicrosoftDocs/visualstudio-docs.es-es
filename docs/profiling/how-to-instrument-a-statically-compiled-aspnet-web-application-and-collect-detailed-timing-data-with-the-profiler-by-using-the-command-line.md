---
title: "C&#243;mo: Instrumentar una aplicaci&#243;n web ASP.NET compilada est&#225;ticamente y recopilar datos detallados de control de tiempo con el generador de perfiles utilizando la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Instrumentar una aplicaci&#243;n web ASP.NET compilada est&#225;ticamente y recopilar datos detallados de control de tiempo con el generador de perfiles utilizando la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de la línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar un componente web precompilado o un sitio web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y recopilar datos detallados de control de tiempo.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos.  Vea [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Para recopilar datos de control de tiempo detallados de un componente web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] utilizando el método de instrumentación, utilice la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente.  En el equipo que hospeda el componente, reemplace la versión no instrumentada del componente por la versión instrumentada.  A continuación, use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno globales de generación de perfiles y reinicie el equipo host.  A continuación, inicie el generador de perfiles.  
  
 Cuando se ejecute el componente instrumentado, los datos de tiempo se recopilarán inmediatamente en un archivo de datos.  Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  
  
 Para finalizar una sesión de generación de perfiles, cierre el proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que hospeda el componente y, a continuación, cierre explícitamente el generador de perfiles.  En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  
  
## Empezar a perfilar  
  
#### Para instrumentar un componente web ASP.NET e iniciar la generación de perfiles  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Utilice la herramienta **VSInstr** para generar una versión instrumentada de la aplicación de destino.  Si es necesario, reemplace los binarios de aplicación del equipo host ASP.NET por los binarios instrumentados.  
  
3.  Inicialice las variables de entorno de generación de perfiles .NET.  En la ventana Símbolo del sistema, escriba:  
  
     **VSPerfClrEnv \/globaltraceon**  
  
4.  Reinicie el equipo.  
  
5.  Abra una ventana de símbolo del sistema.  Si es necesario, establezca la ruta de acceso a las herramientas del generador de perfiles.  
  
6.  Inicie el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   La opción [\/start](../profiling/start.md)**:trace** inicializa el generador de perfiles.  
  
    -   La opción [\/output](../profiling/output.md)**:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **\/start:trace**.  
  
    > [!NOTE]
    >  Las opciones **\/user** y **\/crosssession** son necesarias normalmente para aplicaciones ASP.NET.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/usuario](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET.  Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión.  El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.  Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión.  El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows.  **\/CS** se puede especificar como una abreviatura de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **\/globaloff** a la línea de comandos **\/start**.  Utilice **\/globalon** para reanudar la generación de perfiles.|  
  
7.  Abra el sitio web que contiene el componente instrumentado.  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo mediante el uso de las opciones de **VSPerfCmd.exe**.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso especificado por el identificador del proceso \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) o detiene \(**\/threadoff**\) la recolección de datos del subproceso especificado por el identificador del subproceso \(`TID`\).|  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y, a continuación, use el comando **IISReset** de Internet Information Services \(IIS\) para cerrar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Llame a la opción **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  
  
 El comando **VSPerfClrEnv \/globaloff** borra las variables de entorno de generación de perfiles.  Para que se aplique la configuración de entorno, debe reiniciar el equipo.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Escriba:  
  
     **IISReset \/stop**  
  
3.  Apague el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(Opcional\).  Borre las variables del entorno de generación de perfiles.  Escriba:  
  
     **VSPerfCmd \/globaloff**  
  
5.  Reinicie el equipo.  
  
## Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)