---
title: 'Línea de comandos de generador de perfiles: instrumentación de la aplicación de ASP.NET estática y obtención de los datos de intervalos'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7d743dd854bd11449161c47cc896d0735849e1dd
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778861"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Procedimiento Instrumentar una aplicación web ASP.NET compilada estáticamente y recopilar datos detallados de control de tiempo con el generador de perfiles mediante la línea de comandos
En este artículo se describe cómo usar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar un componente web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] precompilado o un sitio web, y recopilar datos de tiempo detallados.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.
>
> Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Consulte [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Para recopilar datos de tiempo detallados de un componente web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el método de instrumentación, use la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente. En el equipo que hospeda el componente, reemplace la versión no instrumentada del componente por la versión instrumentada. Luego, use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar las variables de entorno globales de generación de perfiles y reinicie el equipo host. A continuación, inicie el generador de perfiles.

 Cuando se ejecute el componente instrumentado, los datos de tiempo se recopilarán inmediatamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.

 Para finalizar una sesión de generación de perfiles, cierre el proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que hospeda el componente y, luego, cierre explícitamente el generador de perfiles. En la mayoría de los casos, recomendamos borrar las variables de entorno de generación de perfiles al final de una sesión.

## <a name="start-to-profile"></a>Empezar a generar perfiles

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Para instrumentar un componente web ASP.NET e iniciar la generación de perfiles

1. Abra una ventana de símbolo del sistema.

2. Utilice la herramienta **VSInstr** para generar una versión instrumentada de la aplicación de destino. Si es necesario, reemplace los binarios de aplicación del equipo host ASP.NET por los binarios instrumentados.

3. Inicialice las variables de entorno de generación de perfiles .NET. En la ventana Símbolo del sistema, escriba:

    **VSPerfClrEnv /globaltraceon**

4. Reinicie el equipo.

5. Abra una ventana de símbolo del sistema. Si es necesario, establezca la ruta de acceso a las herramientas del generador de perfiles.

6. Inicie el generador de perfiles. Tipo:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - La opción [/start](../profiling/start.md) **:trace** inicializa el generador de perfiles.

   - La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar cualquiera de las siguientes opciones con la opción **/start:trace**.

   > [!NOTE]
   > Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.

   | Opción | DESCRIPCIÓN |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña **Procesos** del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **/globaloff** a la línea de comandos **/start**. Utilice **/globalon** para reanudar la generación de perfiles. |

7. Abra el sitio web que contiene el componente instrumentado.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Cuando se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|DESCRIPCIÓN|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia ( **/threadon**) o detiene ( **/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y use el comando **IISReset** de Internet Information Services (IIS) para cerrar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.

 El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles. Para que se aplique la configuración de entorno, debe reiniciar el equipo.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tipo:

    **IISReset /stop**

3. Cierre el generador de perfiles. Tipo:

    **VSPerfCmd /shutdown**

4. (Opcional). Borre las variables del entorno de generación de perfiles. Tipo:

    **VSPerfCmd /globaloff**

5. Reinicie el equipo.

## <a name="see-also"></a>Vea también
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)
