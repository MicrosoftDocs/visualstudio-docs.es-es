---
title: Procedimiento Instrumentar un componente de .NET Framework independiente y recopilar datos de control de tiempo con el generador de perfiles desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 975e9a177f5d9c7423b4c84823464e1a7cc5ad84
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592588"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Procedimiento Instrumentar un componente de .NET Framework independiente y recopilar datos de control de tiempo con el generador de perfiles desde la línea de comandos
En este tema se explica cómo usar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar un componente de .NET Framework, como un archivo *.exe* o *.dll*, y para recopilar datos de tiempo detallados.  

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.  
> 
>  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Para recopilar datos detallados de control de tiempo de un componente de .NET Framework mediante el método de instrumentación, use la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente y la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno de generación de perfiles. A continuación, inicie el generador de perfiles.  

 Cuando se ejecute el componente instrumentado, los datos de tiempo se recopilarán inmediatamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  

 Para finalizar una sesión de generación de perfiles, cierre la aplicación de destino y cierre explícitamente el generador de perfiles. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.  

## <a name="start-the-profiling-session"></a>Iniciar la sesión de generación de perfiles  

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Para iniciar la generación de perfiles utilizando el método de instrumentación  

1. Abra una ventana de símbolo del sistema. Si es necesario, agregue el directorio de herramientas del generador de perfiles a la variable de entorno PATH. La ruta de acceso no se agrega en la instalación.  

2. Utilice la herramienta **VSInstr** para generar una versión instrumentada de la aplicación de destino.  

3. Inicialice las variables de entorno de generación de perfiles de .NET Framework. Tipo:  

    **VSPerfClrEnv /traceon**  

4. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  

   - La opción [/start](../profiling/start.md)**:trace** inicializa el generador de perfiles.  

   - La opción [/output](../profiling/output.md)**:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede usar cualquiera de las opciones siguientes con la opción **/start:trace**.  

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna **Id. de sesión** de la pestaña **Procesos** del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Inicia el generador de perfiles con la recolección de datos en pausa. Utilice [/globalon](../profiling/globalon-and-globaloff.md) para reanudar la generación de perfiles. |
   | [/counter](../profiling/counter.md) **:** `Config` | Recopila información del contador de rendimiento del procesador especificado en `Config`. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente. |


5. Inicie la aplicación de destino desde la ventana del símbolo del sistema.  

## <a name="control-data-collection"></a>Controlar la recopilación de datos  
 Durante la ejecución de la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|  

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación que está ejecutando el componente instrumentado. Llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1.  Cierre la aplicación de destino.  

2.  Cierre el generador de perfiles. Tipo:  

     **VSPerfCmd /shutdown**  

3.  (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:  

     **VSPerfClrEnv /off**  

## <a name="see-also"></a>Vea también  
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)