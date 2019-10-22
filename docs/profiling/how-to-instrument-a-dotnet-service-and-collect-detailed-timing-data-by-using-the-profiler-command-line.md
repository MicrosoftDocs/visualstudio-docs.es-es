---
title: 'Línea de comandos de generador de perfiles: instrumentación del servicio de. NET y obtención de los detalles de intervalos'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4f3e03a35719e6dd1cbfa7514a304539dc4f0ca1
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67032050"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Procedimiento Instrumentar un servicio .NET y recopilar datos detallados de control de tiempo mediante la línea de comandos del generador de perfiles

En este artículo se explica cómo usar las herramientas de línea de comandos de Herramientas de generación de perfiles de Visual Studio para instrumentar un servicio de .NET Framework y recopilar datos de tiempo detallados.

> [!NOTE]
> No puede generar perfiles de un servicio con el método de instrumentación si el servicio no se puede reiniciar después de iniciar el equipo, como por ejemplo un servicio que se inicia solamente cuando se inicia el sistema operativo.
>
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.
>
> Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Para recopilar datos de tiempo detallados de un servicio de .NET Framework mediante el método de instrumentación, use la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente. A continuación, reemplace la versión no instrumentada del servicio por la versión instrumentada, asegurándose de que el servicio se configura para iniciarse manualmente. A continuación, use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno globales de generación de perfiles y, a continuación, reinicie el equipo host. A continuación, inicie el generador de perfiles.

Cuando se inicia el servicio, los datos de control de tiempo se recopilan automáticamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.

Para finalizar una sesión de generación de perfiles, desactive el servicio y, a continuación, apague explícitamente el generador de perfiles. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="start-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles

1. Abra una ventana de símbolo del sistema.

2. Use la herramienta **VSInstr** para generar una versión instrumentada del archivo binario del servicio.

3. Reemplace el archivo binario original por la versión instrumentada. En el Administrador de control de servicios de Windows, asegúrese de que el Tipo de inicio del servicio está establecido en Manual.

4. Inicialice las variables de entorno de generación de perfiles de .NET Framework. Tipo:

     **VSPerfClrEnv /globaltraceon**

5. Reinicie el equipo.

6. Abra una ventana de símbolo del sistema.

7. Inicie el generador de perfiles. Tipo:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - La opción [/start](../profiling/start.md) **:trace** inicializa el generador de perfiles.

   - La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.*vsp*).

     Puede usar cualquiera de las opciones siguientes con la opción **/start:trace**.

     > [!NOTE]
     > Normalmente, las opciones **/user** y **/crosssession** son necesarias para la generación de perfiles de servicios.

     | Opción | DESCRIPCIÓN |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
     | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna **Id. de sesión** de la pestaña **Procesos** del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
     | [/waitstart](../profiling/waitstart.md)[ **:** `Interval`] | Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error. Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente. De manera predeterminada, **/start** termina inmediatamente. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **/globaloff** a la línea de comandos **/start**. Utilice **/globalon** para reanudar la generación de perfiles. |
     | [/counter](../profiling/counter.md) **:** `Config` | Recopila información del contador de rendimiento del procesador especificado en Config. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente. |

8. Inicie el servicio en el Administrador de control de servicios de Windows.

## <a name="control-data-collection"></a>Controlar la recopilación de datos

Cuando se está ejecutando el servicio, puede usar las opciones de *VSPerfCmd.exe* para iniciar y detener la escritura de datos en el archivo de datos del generador de perfiles. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de un servicio.

- Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|DESCRIPCIÓN|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia ( **/threadon**) o detiene ( **/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles

Para finalizar una sesión de generación de perfiles, detenga el servicio que está ejecutando el componente instrumentado y, a continuación, llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles.

Para que se aplique la configuración de entorno, debe reiniciar el equipo.

1. Detenga el servicio en el Administrador de control de servicios.

2. Cierre el generador de perfiles. Tipo:

     **VSPerfCmd /shutdown**

3. Cuando haya finalizado la generación de perfiles, borre las variables de entorno de generación de perfiles. Tipo:

     **VSPerfClrEnv /globaloff**

4. Reemplace el módulo instrumentado con el original. Si es necesario, vuelva a configurar el Tipo de inicio del servicio.

5. Reinicie el equipo.

## <a name="see-also"></a>Vea también

[Profile services](../profiling/command-line-profiling-of-services.md) (Servicios de generación de perfiles)
[Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)
