---
title: "C&#243;mo: Iniciar una aplicaci&#243;n nativa independiente con el generador de perfiles para recopilar datos de simultaneidad utilizando la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Iniciar una aplicaci&#243;n nativa independiente con el generador de perfiles para recopilar datos de simultaneidad utilizando la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar una aplicación independiente \(cliente\) nativa y recopilar datos de simultaneidad de procesos y de subprocesos.  
  
 Una sesión de generación de perfiles tiene las partes siguientes:  
  
-   Iniciar la aplicación con el generador de perfiles  
  
-   Controlar la recolección de datos  
  
-   Finalizar la sesión de generación de perfiles  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits.  Para utilizar el generador de perfiles en un símbolo del sistema, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana **Símbolo del sistema** o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Iniciar la aplicación con el generador de perfiles  
 Para iniciar una aplicación de destino con el generador de perfiles, utilice las opciones **\/start** y **\/launch** de [VSPerfCmd.exe](../profiling/vsperfcmd.md) para inicializar el generador de perfiles e iniciar la aplicación.  Puede especificar **\/start** y **\/launch** y sus opciones respectivas.  También puede agregar la opción **\/globaloff** para pausar la recolección de datos al inicio de la aplicación de destino.  A continuación, utilice **\/globalon** para empezar a recopilar datos.  
  
#### Para iniciar una aplicación con el generador de perfiles  
  
1.  En un símbolo del sistema, escriba el siguiente comando:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     La opción [\/output](../profiling/output.md)**:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede usar cualquiera de las opciones de la tabla siguiente con la opción **\/start:concurrency** .  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
  
2.  Inicie la aplicación de destino escribiendo:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     Puede utilizar cualquiera de las opciones de la tabla siguiente con la opción **\/launch**.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Especifica una cadena que contiene los argumentos de la línea de comandos que se van a pasar a la aplicación de destino.|  
    |[\/console](../profiling/console.md)|Inicia la aplicación de línea de comandos de destino en otra ventana.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Especifica la versión del Common Language Runtime \(CLR\) para la generación de perfiles si la aplicación carga más de una versión del CLR.|  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los pares de opciones de la tabla siguiente inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso que especifica el identificador de proceso \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso \(`PID`\) o por el nombre de proceso \(*ProcName*\).  **\/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
-   También puede usar la opción **VSPerfCmd.exe**[\/mark](../profiling/mark.md) para insertar una marca de generación de perfiles en el archivo de datos.  El comando **\/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario.  Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles.  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos.  Puede dejar de recopilar datos de simultaneidad cerrando la aplicación para la que se generan perfiles o invocando la opción **VSPerfCmd \/detach**.  Después invoque la opción **VSPerfCmd \/shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Desasocie el generador de perfiles de la aplicación de destino cerrándolo o escribiendo el siguiente comando en un símbolo del sistema:  
  
     **VSPerfCmd \/detach**  
  
2.  Apague el generador de perfiles escribiendo el siguiente comando en un símbolo del sistema:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)