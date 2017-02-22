---
title: "C&#243;mo: Adjuntar el generador de perfiles a un servicio nativo para recopilar datos de simultaneidad utilizando la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Adjuntar el generador de perfiles a un servicio nativo para recopilar datos de simultaneidad utilizando la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a un servicio nativo \(C\/C\+\+\) y recopilar datos de simultaneidad de procesos y subprocesos utilizando el método de muestreo.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de Visual Studio.  En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits.  Para utilizar el generador de perfiles en un símbolo del sistema, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana **Símbolo del sistema** o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Mientras el generador de perfiles está asociado al servicio, puede pausar y reanudar la recolección de datos.  Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto al servicio y debe apagarse explícitamente.  
  
## Adjuntar el generador de perfiles  
 Para adjuntar el generador de perfiles a un servicio nativo, utilice las opciones **\/start** y **\/attach** de **VSPerfCmd** para inicializar el generador de perfiles y adjuntarlo a la aplicación de destino.  Puede especificar **\/start** y **\/attach** y sus opciones respectivas en una línea de comandos única.  También puede agregar la opción **\/globaloff** para pausar la recolección de datos al inicio de la aplicación de destino.  A continuación, utilice **\/globalon** para empezar a recopilar datos.  
  
#### Para adjuntar el generador de perfiles a un servicio nativo  
  
1.  Si el servicio no se está ejecutando, inícielo.  
  
2.  Escriba la siguiente cadena en un símbolo del sistema para iniciar el generador de perfiles:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   La opción [\/output](../profiling/output.md)**:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede utilizar cualquier opción de la tabla siguiente con la opción **\/start** .  
  
    > [!NOTE]
    >  La mayoría de los servicios requieren las opciones **\/user** y **\/crosssession**.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Especifica el dominio y el nombre de usuario opcionales de la cuenta a la que se va a conceder acceso al generador de perfiles.|  
    |[\/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows \(ETW\) que se va a recopilar durante la generación de perfiles.  Los eventos ETW se recopilan en un archivo \(.etl\) independiente.|  
  
3.  Adjunte el generador de perfiles al servicio escribiendo el comando siguiente en un símbolo del sistema:  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` especifica el identificador o nombre de proceso de la aplicación de destino.  Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los pares de opciones de la tabla siguiente inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos del proceso que especifica el identificador de proceso \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso \(`PID`\) o por el nombre de proceso \(*ProcName*\).  **\/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos.  Puede detener la recolección de datos de un servicio nativo que se perfila con el método de simultaneidad deteniendo el servicio o invocando la opción **VSPerfCmd \/detach**.  Después invoque la opción **VSPerfCmd \/shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Desasocie el generador de perfiles de la aplicación de destino deteniendo el servicio o escribiendo el siguiente comando en un símbolo del sistema:  
  
     Escriba **VSPerfCmd \/detach**  
  
2.  Apague el generador de perfiles escribiendo el siguiente comando en un símbolo del sistema:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)