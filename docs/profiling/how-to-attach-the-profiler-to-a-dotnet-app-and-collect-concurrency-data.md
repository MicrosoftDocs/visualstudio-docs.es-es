---
title: Asociación del generador de perfiles a .NET para recopilar datos de simultaneidad
description: Obtenga información sobre cómo obtener datos de simultaneidad de procesos y subprocesos mediante las herramientas de línea de comandos de las Herramientas de generación de perfiles de Visual Studio para asociar el generador de perfiles a una aplicación .NET Framework en ejecución.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f3eb5fbed055ef79595947954f86159b9cb2efc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958913"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Procedimiento para asociar el generador de perfiles a una aplicación independiente de .NET Framework para recopilar datos de simultaneidad mediante la línea de comandos
En este artículo se describe cómo utilizar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a una aplicación independiente (cliente) de .NET Framework en ejecución y recopilar datos de simultaneidad de proceso y subproceso.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Tutorial: Uso de las API del generador de perfiles](../profiling/walkthrough-using-profiler-apis.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana del símbolo del sistema o agregarla al propio comando. Para más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya asociado a la aplicación y debe cerrarse explícitamente.

## <a name="attach-the-profiler"></a>Anexión del generador de perfiles

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Para adjuntar el Generador de perfiles a una aplicación .NET Framework en ejecución

1. Abra una ventana de símbolo del sistema.

2. Inicie el generador de perfiles. Tipo:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar cualquiera de las siguientes opciones con la opción **/start:concurrency**.

    |Opción|Descripción|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|

3. Inicie la aplicación de destino de la manera habitual.

4. Adjunte el generador de perfiles a la aplicación de destino. Tipo:

     **VSPerfCmd /attach:** `PID` [ **/lineoff**] [ **/targetclr:** `Version`]

    - `PID` especifica el identificador de proceso de la aplicación de destino. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

    - [/lineoff](../profiling/lineoff.md) deshabilita la recopilación de datos de número de línea.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recopilación de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de la aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones de *VSPerfCmd.exe* inician y detienen la recopilación de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** inicia la recopilación de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (ProcName). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Puede dejar de recopilar datos de una aplicación para la que se ha ejecutado la generación de perfiles con el método de simultaneidad cerrando la aplicación o invocando la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino.

    - Escriba **VSPerfCmd /detach**

         o bien

    - Cierre la aplicación de destino.

2. Cierre el generador de perfiles. Tipo:

     VSPerfCmd[/shutdown](../profiling/shutdown.md)
