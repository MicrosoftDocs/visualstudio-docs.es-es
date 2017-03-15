---
title: "C&#243;mo: Adjuntar el generador de perfiles a una aplicaci&#243;n independiente de .NET Framework para recopilar datos mediante la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Adjuntar el generador de perfiles a una aplicaci&#243;n independiente de .NET Framework para recopilar datos mediante la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] para adjuntar el generador de perfiles a una aplicación independiente \(cliente\) de .NET Framework en ejecución y recopilar datos de memoria.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para adjuntar el generador de perfiles a una aplicación de .NET Framework y recopilar datos de memoria, debe utilizar la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas antes de iniciar la aplicación de destino.  Mientras el generador de perfiles está adjunto a la aplicación, puede utilizar la herramienta **VSPerfCmd.exe** para pausar y reanudar la recolección de datos.  
  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente.  En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  
  
## Adjuntar el generador de perfiles  
  
#### Para adjuntar el Generador de perfiles a una aplicación .NET Framework que se esté ejecutando  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Inicialice las variables de entorno de generación de perfiles.  Escriba:  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   Las opciones **\/samplegc** y **\/samplegclife** especifican si solamente se recopilan datos de asignación de memoria o si se recopilan tanto datos de asignación de memoria como datos de duración de objetos.  Se debe especificar una única opción.  
  
        |Opción|Descripciones|  
        |------------|-------------------|  
        |**\/samplegc**|Solamente recopila datos de asignación de memoria.|  
        |**\/samplegclife**|Recopila datos de asignación de memoria y datos de duración de objetos.|  
  
    -   La opción **\/samplelineoff** deshabilita la recopilación de datos de número de línea de código fuente.  
  
3.  Inicie el generador de perfiles.  Escriba:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   La opción [\/start](../profiling/start.md)**:sample** inicializa el generador de perfiles.  
  
    -   La opción [\/output](../profiling/output.md)**:**`OutputFile` es necesaria con **\/start**.  `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles \(.vsp\).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **\/start:sample**.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/usuario](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles.  Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión.  El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otras sesiones.  Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente.  El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows.  **\/CS** se puede especificar como una abreviatura de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Se utiliza únicamente con **\/wincounter**.  Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows.  El valor predeterminado es 500 ms.|  
  
4.  Si es necesario, inicie la aplicación de destino de la manera típica.  
  
5.  Adjunte el generador de perfiles a la aplicación de destino.  Escriba:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` especifica el identificador de proceso de la aplicación de destino.  `ProcessName` especifica el nombre del proceso.  Tenga en cuenta que si especifica `ProcessName` y se están ejecutando varios procesos con el mismo nombre, los resultados son imprevisibles.  Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  
  
    -   **\/targetclr:** `Version` especifica la versión de Common Language Runtime \(CLR\) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.  Opcional.  
  
## Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo mediante el uso de las opciones de **VSPerfCmd.exe**.  Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones inician y detienen la recolección de datos.  Especifique cada opción en una línea de comandos diferente.  Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) o detiene \(**\/globaloff**\) la recolección de datos de todos los procesos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) o detiene \(**\/processoff**\) la recolección de datos para el proceso especificado por el `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia la recolección de datos para el proceso especificado por `PID` o por el nombre de proceso \(ProcName\).  **\/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
## Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente.  Puede desasociar el generador de perfiles de una aplicación cuyo perfil se ha generado mediante el método de muestreo, el cierre de la aplicación o una llamada al método **VSPerfCmd \/detach**.  Después debe llamar a la opción **VSPerfCmd \/shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  El comando **VSPerfClrEnv \/off** borra las variables de entorno de generación de perfiles.  
  
#### Para finalizar una sesión de generación de perfiles  
  
1.  Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:  
  
    -   Escriba **VSPerfCmd \/detach**  
  
         O bien  
  
    -   Cierre la aplicación de destino.  
  
2.  Apague el generador de perfiles.  Escriba:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Opcional\) Borre las variables del entorno de generación de perfiles.  Escriba:  
  
     **VSPerfCmd \/off**  
  
## Vea también  
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)