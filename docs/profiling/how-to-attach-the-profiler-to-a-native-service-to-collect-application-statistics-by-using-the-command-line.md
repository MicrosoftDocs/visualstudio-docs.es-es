---
title: asociación del generador de perfiles a un servicio para obtener estadísticas de aplicaciones
description: Use las Herramientas de generación de perfiles de Visual Studio desde la línea de comandos para recopilar estadísticas de rendimiento de un servicio nativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 27c3c0f71f883c85718abbbfee5d54dd625381d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886345"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line-vsperfcmd"></a>Procedimiento Asociación del generador de perfiles a un servicio nativo para recopilar estadísticas de aplicación mediante la línea de comandos (VSPerfCmd)
En este artículo se describe cómo usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a un servicio nativo y recopilar estadísticas de rendimiento mediante el método de muestreo.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

 Mientras el generador de perfiles está adjunto al servicio, puede pausar y reanudar la recolección de datos.

 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar del servicio y se debe cerrar explícitamente.

## <a name="start-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles
 Para adjuntar el generador de perfiles a un servicio nativo, use las opciones [/start](../profiling/start.md) y [/attach](../profiling/attach.md) de **VSPerfCmd.exe** para inicializar el generador de perfiles y adjuntarlo a la aplicación de destino. Puede especificar **/start** y **/attach** y sus respectivas opciones en una línea de comandos única. También puede agregar la opción [/globaloff](../profiling/globalon-and-globaloff.md) para pausar la recolección de datos en el inicio de la aplicación de destino. Después, puede usar [/globalon](../profiling/globalon-and-globaloff.md) para empezar a recopilar los datos.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Para adjuntar el generador de perfiles a un servicio nativo

1. Si es necesario, inicie el servicio.

2. Abra una ventana de símbolo del sistema.

3. Inicie el generador de perfiles. Tipo:

    **VSPerfCmd /start:sample** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - La opción **/start:sample** inicializa el generador de perfiles.

   - La opción **/output:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.*vsp*).

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.

   > [!NOTE]
   > Normalmente, las opciones **/user** y **/crosssession** son necesarias para servicios.

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente. |

4. Adjunte el generador de perfiles al servicio. Tipo:

    **VSPerfCmd /attach:** `PID` [`Sample Event`]

    `PID` especifica el identificador de proceso de la aplicación de destino. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

    De manera predeterminada, se realiza un muestreo de los datos de rendimiento cada 10.000.000 ciclos de reloj de procesador no detenidos. Esto equivale aproximadamente a una vez cada 10 segundos en un procesador de 1 GHz. Puede especificar una de las siguientes opciones para cambiar el intervalo del ciclo de reloj o especificar otro evento de muestreo.

   |Evento de muestreo|Descripción|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|Cambia el intervalo de muestreo al número de ciclos de reloj no detenidos especificado en `Interval`.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|Cambia el evento de muestreo a errores de página. Si se especifica `Interval`, se establece el número de errores de página entre un muestreo y otro. El valor predeterminado es 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [ **:** `Interval`]|Cambia el evento de muestreo a llamadas al sistema por parte del proceso al kernel del sistema operativo (llamadas syscall). Si se especifica `Interval`, se establece el número de llamadas entre un muestreo y otro. El valor predeterminado es 10.|
   |[/counter](../profiling/counter.md) **:** `Config`|Cambia el evento y el intervalo de muestreo al contador de rendimiento del procesador y al intervalo especificados en `Config`.|

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Mientras la aplicación de destino se está ejecutando, puede usar las opciones de *VSPerfCmd.exe* para iniciar y detener la escritura de datos en el archivo de datos del generador de perfiles. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso o por el nombre de proceso. **/detach** detiene la recopilación de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar del servicio y se debe apagar explícitamente. Puede desasociar el servicio nativo para el que se está realizando la generación de perfiles con el método de muestreo deteniendo el servicio o llamando a la opción **VSPerfCmd /detach**. Después, llame a la opción **VSPerfCmd** [/shutdown](../profiling/shutdown.md) para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino:

    - Detenga el servicio.

         o bien

    - Escriba **VSPerfCmd /detach**

2. Cierre el generador de perfiles. Tipo:

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Vea también
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
- [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)
