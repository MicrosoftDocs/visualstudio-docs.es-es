---
title: 'Cómo: Instrumentar un componente de .NET Framework independiente y recopilar datos de memoria con el generador de perfiles utilizando la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce9538db2dae800a84eee26cd4540ca8be33a299
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592557"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Cómo: Instrumentar un componente de .NET Framework independiente y recopilar datos de memoria con el generador de perfiles utilizando la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: Instrumentar un componente de .NET Framework de independiente y recopilar datos de memoria con el Profiler mediante el uso de la línea de comandos](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line).  
  
En este tema se describe cómo utilizar las herramientas de la línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para instrumentar un componente .NET Framework de una aplicación independiente como un archivo .exe o .dll y recopilar información de la memoria utilizando el generador de perfiles.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de Visual Studio. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para recopilar datos de memoria de un componente .NET Framework utilizando el método de instrumentación, utilice la herramienta [VSInstr.exe](../profiling/vsinstr.md) para compilar una versión instrumentada del componente y la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno de generación de perfiles. Después, inicie el generador de perfiles utilizando la herramienta **VSPerfCmd.exe**.  
  
 Cuando se ejecute el componente instrumentado, los datos de memoria se recopilarán inmediatamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  
  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación de destino y cierre explícitamente el generador de perfiles. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  
  
## <a name="starting-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Para adjuntar el Generador de perfiles a una aplicación .NET Framework que se esté ejecutando  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Utilice la herramienta **VSInstr** para generar una versión instrumentada de la aplicación de destino.  
  
3.  Inicialice las variables de entorno de generación de perfiles de .NET Framework. Tipo:  
  
     **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}  
  
    -   Las opciones **/tracegc** y **/tracegclife** inicializan las variables de entorno para recopilar solamente datos de asignación de memoria o recopilar tanto datos de asignación de memoria como datos de duración de objetos.  
  
        |Opción|Descripción|  
        |------------|-----------------|  
        |**/tracegc**|Habilita la recopilación exclusiva de datos de asignación de memoria.|  
        |**/tracegclife**|Habilita la recopilación tanto de datos de asignación de memoria como de datos de duración de objetos.|  
  
4.  Inicie el generador de perfiles. Tipo:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   La opción [/start](../profiling/start.md)**:trace** inicializa el generador de perfiles.  
  
    -   La opción [/output](../profiling/output.md)**:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **/start:trace**.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **/globaloff** a la línea de comandos **/start**. Utilice **/globalon** para reanudar la generación de perfiles.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Recopila información del contador de rendimiento del procesador especificado en Config. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles.|  
    |[events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|  
  
5.  Inicie la aplicación de destino desde la ventana del símbolo del sistema.  
  
## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de **VSPerfCmd.exe**. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recolección de datos para el proceso especificado por el identificador de subproceso (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión generación de perfiles, cierre la aplicación que está ejecutando el componente instrumentado y, a continuación, llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.  
  
#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  
  
1.  Cierre la aplicación de destino.  
  
2.  Cierre el generador de perfiles. Tipo:  
  
     **VSPerfCmd /shutdown**  
  
3.  (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:  
  
     **VSPerfCmd /off**  
  
## <a name="see-also"></a>Vea también  
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)



