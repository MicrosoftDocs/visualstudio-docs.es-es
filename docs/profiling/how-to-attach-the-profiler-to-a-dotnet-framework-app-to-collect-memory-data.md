---
title: Asociación del generador de perfiles a una aplicación de .NET para recopilar datos de memoria
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779134"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Procedimiento para adjuntar el generador de perfiles a una aplicación de .NET Framework independiente para recopilar datos de memoria mediante la línea de comandos

En este artículo se describe cómo usar las herramientas de línea de comandos de las Herramientas de generación de perfiles de Visual Studio para adjuntar el generador de perfiles a una aplicación independiente (cliente) de .NET Framework en ejecución y recopilar datos de memoria.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

Para adjuntar el generador de perfiles a una aplicación de .NET Framework y recopilar datos de memoria, debe usar la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas antes de iniciar la aplicación de destino. Mientras el generador de perfiles está adjunto a la aplicación, puede usar la herramienta *VSPerfCmd.exe* para pausar y reanudar la recolección de datos.

Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="attach-the-profiler"></a>Anexión del generador de perfiles

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Para adjuntar el Generador de perfiles a una aplicación .NET Framework en ejecución

1. Abra una ventana de símbolo del sistema.

2. Inicialice las variables del entorno de generación de perfiles. Tipo:

     **VSPerfClrEnv** { **/samplegc** &#124; **/samplegclife**} [ **/samplelineoff**]

    - Las opciones **/samplegc** y **/samplegclife** especifican si solamente se recopilan datos de asignación de memoria o si se recopilan tanto datos de asignación de memoria como datos de duración de objetos. Se debe especificar una única opción.

        |Opción|Descripciones|
        |------------|------------------|
        |**/samplegc**|Solamente recopila datos de asignación de memoria.|
        |**/samplegclife**|Recopila datos de asignación de memoria y datos de duración de objetos.|

    - La opción **/samplelineoff** deshabilita la recopilación de datos de número de línea de código fuente.

3. Inicie el generador de perfiles. Tipo:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - La opción [/start](../profiling/start.md) **:sample** inicializa el generador de perfiles.

   - La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.

     | Opción | Descripción |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |

4. Si es necesario, inicie la aplicación de destino de la manera típica.

5. Adjunte el generador de perfiles a la aplicación de destino. Tipo:

     **VSPerfCmd** [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` especifica el identificador de proceso de la aplicación de destino. `ProcessName` especifica el nombre del proceso. Tenga en cuenta que si especifica `ProcessName` y se están ejecutando varios procesos con el mismo nombre, los resultados son imprevisibles. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

    - **/targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.

## <a name="control-data-collection"></a>Controlar la recopilación de datos

Cuando se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recopilación de datos para el proceso especificado por `PID`.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por `PID` o por el nombre de proceso (ProcName). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles

Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente. Puede desasociar el generador de perfiles de una aplicación cuyo perfil se ha generado mediante el método de muestreo, el cierre de la aplicación o una llamada la opción **VSPerfCmd /detach**. Después, llame a la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.

### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:

    - Escriba **VSPerfCmd /detach**

         o bien

    - Cierre la aplicación de destino.

2. Cierre el generador de perfiles. Tipo:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:

     **VSPerfCmd /off**

## <a name="see-also"></a>Vea también

[Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
[Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)
