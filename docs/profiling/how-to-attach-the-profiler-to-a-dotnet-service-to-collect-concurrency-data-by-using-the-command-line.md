---
title: 'Asociación del generador de perfiles a .NET para recopilar datos de simultaneidad: línea de comandos'
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 7b9b2e9a90df1b9dcfaaa2fd7b77410e24e32a9a
ms.sourcegitcommit: 822e61c69514e9f564d37ba6ca6832ccf7fbc60d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421812"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Procedimiento Asociar el generador de perfiles a un servicio .NET para recopilar datos de simultaneidad mediante la línea de comandos
En este artículo se explica cómo usar las herramientas de línea de comandos de Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a un servicio de .NET Framework y recopilar datos de simultaneidad de procesos y subprocesos mediante el método de muestreo.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

 Para recopilar datos de simultaneidad, adjunte el generador de perfiles al proceso del servicio. Mientras el generador de perfiles está adjunto al servicio, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles ya no debe estar conectado al servicio y se debe apagar de forma explícita. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="attach-the-profiler"></a>Anexión del generador de perfiles

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Para adjuntar el generador de perfiles a un servicio de .NET Framework

1. Instale el servicio.

2. Abra una ventana de comandos.

3. Inicialice las variables del entorno de generación de perfiles. Tipo:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [ **/samplelineoff**]

    - **/globalsampleon** habilita el muestreo.

    - **/samplelineoff** desactiva la asignación de los datos recopilados a líneas de código fuente específicas. Cuando se especifica esta opción, los datos se asignan solo a funciones.

4. Reinicie el equipo.

5. Inicie el generador de perfiles. Tipo:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede utilizar cualquiera de las siguientes opciones con la opción **/start**.

    > [!NOTE]
    > Normalmente, las opciones **/user** y **/crosssession** son necesarias para servicios.

    |Opción|Descripción|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows.|
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si el servicio se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna **Id. de sesión** de la pestaña **Procesos** del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente.|

6. Si es necesario, inicie el servicio.

7. Adjunte el generador de perfiles al servicio. Tipo:

     **VSPerfCmd /attach:** `PID` [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` especifica el identificador de proceso o el nombre del servicio. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

    - **targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Mientras se ejecuta el servicio, puede controlar la recolección de datos si inicia o detiene la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de la aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso o por el nombre de proceso. **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

- También puede utilizar la opción [/mark](../profiling/mark.md) de **VSPerfCmd.exe** para insertar una marca de generación de perfiles en el archivo de datos. El comando **/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario. Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles. Los siguientes pares de opciones de VSPerfCmd inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Puede dejar de recopilar datos de una aplicación para la que se ha ejecutado la generación de perfiles con el método de simultaneidad deteniendo el servicio o invocando la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino.

    - Detenga el servicio.

         o bien

    - Escriba **VSPerfCmd /detach**.

2. Cierre el generador de perfiles. Tipo:

     **VSPerfCmd** [Shutdown](../profiling/shutdown.md)
