---
title: Asociación del generador de perfiles a un servicio de .NET Framework para recopilar datos de memoria
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 579579c24355a3bcc240a710c07f2163b5b5c231
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630566"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Procedimiento Asociar el generador de perfiles a un servicio .NET para recopilar datos de memoria mediante la línea de comandos
En este artículo se describe cómo usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a un servicio de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y recopilar datos de memoria. Puede recopilar datos sobre el número y tamaño de asignaciones de memoria, así como recopilar datos sobre la duración de objetos de memoria.

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
>  Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

 Para recopilar datos de memoria de un servicio de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno adecuadas en el equipo que hospeda el servicio. El equipo se debe reiniciar para configurarlo para la generación de perfiles.

 Después, use la herramienta [VSPerfCmd](../profiling/vsperfcmd.md) para adjuntar el generador de perfiles al proceso del servicio. Mientras el generador de perfiles está adjunto al servicio, puede pausar y reanudar la recolección de datos.

 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar del servicio y se debe cerrar explícitamente. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="attach-the-profiler"></a>Anexión del generador de perfiles

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Para adjuntar el generador de perfiles a un servicio de .NET Framework

1. Si es necesario, instale el servicio.

2. Abra una ventana de símbolo del sistema.

3. Inicialice las variables del entorno de generación de perfiles. Tipo:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - Las opciones **/globalsamplegclife** y **/globalsamplegclife** especifican el tipo de datos de memoria que se van a recopilar. Especifique una y solamente una de las siguientes opciones.

     **/globalsamplegc** Habilita la recopilación de datos de asignación de memoria.

     **/globalsamplegclife** Habilita la recopilación tanto de datos de asignación de memoria como de datos de duración de objetos.

   - La opción **/samplelineoff** deshabilita la recopilación de datos de número de línea de código fuente.

4. Reinicie el equipo para establecer la nueva configuración de entorno.

5. Si es necesario, inicie el servicio.

6. Abra una ventana de símbolo del sistema. Si es necesario, agregue la ruta de acceso del generador de perfiles a la variable de entorno PATH.

7. Inicie el generador de perfiles. Tipo:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - La opción **/start:sample** inicializa el generador de perfiles.

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar una o varias de las opciones siguientes con la opción **/start:sample**.

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para servicios.

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio opcional y nombre de usuario de la cuenta de inicio de sesión bajo la que se ejecuta el servicio. La cuenta de inicio de sesión se muestra en la columna Iniciar sesión como del Administrador de control de servicios de Windows. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otros inicios de sesión. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente. |


8. Adjunte el generador de perfiles al servicio. Tipo:

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]

   -   Especifique el identificador del proceso o el nombre del proceso del servicio. Puede ver los nombres e identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

   -   **targetclr:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Opcional.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Mientras se está ejecutando el servicio, puede usar las opciones de *VSPerfCmd.exe* para detener e iniciar la escritura de datos en el archivo de datos del generador de perfiles. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución del programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso o por el nombre de proceso. **/detach** detiene la recopilación de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Puede detener la recopilación de datos de una aplicación de generación de perfiles con el método de muestreo deteniendo el servicio o llamando a la opción **VSPerfCmd /detach**. Después, llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1.  Siga uno de estos procedimientos para desasociar el generador de perfiles de la aplicación de destino:

    -   Detenga el servicio.

         o bien

    -   Escriba **VSPerfCmd /detach**

2.  Cierre el generador de perfiles. Tipo:

     **VSPerfCmd /shutdown**

3.  (Opcional) Borre las variables del entorno de generación de perfiles. Tipo:

     **VSPerfClrEnv /globaloff**

4.  Reinicie el equipo.

## <a name="see-also"></a>Vea también
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
- [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)