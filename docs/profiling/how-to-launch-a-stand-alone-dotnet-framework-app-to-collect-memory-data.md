---
title: 'Línea de comandos de generador de perfiles: apertura de la aplicación cliente de .NET Framework y obtención de los datos de memoria'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c9ee0ae59fd32394e31acc75184d0e55aaae872d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775365"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Procedimiento Iniciar una aplicación de .NET Framework independiente con el generador de perfiles para recopilar datos de memoria mediante la línea de comandos
En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar una aplicación independiente (cliente) de .NET Framework y recopilar datos de memoria.

 Una sesión de generación de perfiles tiene tres partes:

- Iniciar la aplicación mediante el generador de perfiles.

- Recopilar datos de generación de perfiles.

- Finalizar la sesión de generación de perfiles.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

## <a name="start-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles
 Para iniciar una aplicación de destino con el generador de perfiles, utilice las opciones **VSPerfCmd.exe/start** y **/launch** para inicializar el generador de perfiles e iniciar la aplicación. Puede especificar **/start** y **/launch** y sus respectivas opciones en una línea de comandos única.

 También puede agregar las opciones **/globaloff** para pausar la recolección de datos en el inicio de la aplicación de destino. Después, use **/globalon** para empezar a recopilar datos.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Para iniciar una aplicación mediante el generador de perfiles

1. Abra una ventana de símbolo del sistema.

2. Inicie el generador de perfiles. Tipo:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - La opción [/start](../profiling/start.md) **:sample** inicializa el generador de perfiles.

   - La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).

     Puede usar cualquiera de las siguientes opciones con la opción **/start:sample**.

   | Opción | Descripción |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |

3. Inicie la aplicación de destino. Tipo:

    **VSPerfCmd** [/launch](../profiling/launch.md) **:** `appName` **/gc:** {**allocation**&#124;**lifetime**}[`Options`]

   - La opción [/gc](../profiling/gc-vsperfcmd.md) **:** `Keyword` es necesaria para recopilar datos de memoria de .NET Framework. El parámetro de palabra clave especifica si se recopilan datos de asignación de memoria o si se recopilan tanto datos de asignación de memoria como datos de duración de objetos.

     |Palabra clave|Descripción|
     |-------------|-----------------|
     |**allocation**|Solo recopila datos de asignación de memoria.|
     |**lifetime**|Recopila datos de asignación de memoria y datos de duración de objetos.|

     Puede usar cualquiera de las siguientes opciones con la opción **/launch**.

   |Opción|Descripción|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:** `Arguments`|Especifica una cadena que contiene los argumentos de la línea de comandos que se van a pasar a la aplicación de destino.|
   |[/console](../profiling/console.md)|Inicia la aplicación de línea de comandos de destino en otra ventana.|
   |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación.|

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Cuando se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** inicia la recolección de datos para el proceso especificado por `PID` (el Id. de proceso). **/detach** detiene la recolección de datos de todos los procesos.|

- También puede utilizar la opción [/mark](../profiling/mark.md) de **VSPerfCmd.exe** para insertar una marca de generación de perfiles en el archivo de datos. El comando **/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario. Las marcas se pueden utilizar para filtrar los datos.

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar una sesión de generación de perfiles, el generador de perfiles se debe desasociar de todos los procesos perfilados y se debe apagar explícitamente. Puede desasociar el generador de perfiles de una aplicación cuyo perfil se ha generado mediante el método de muestreo, el cierre de la aplicación o una llamada la opción **VSPerfCmd /detach**. Después, llame a la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /off** borra las variables de entorno de generación de perfiles.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Realice uno de los pasos siguientes para desasociar el generador de perfiles de la aplicación de destino:

    - Cierre la aplicación de destino.

         o bien

    - Escriba **VSPerfCmd /detach**

2. Cierre el generador de perfiles. Tipo:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Vea también
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)
