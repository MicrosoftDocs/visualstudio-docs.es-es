---
title: Procedimiento Instrumentar un servicio nativo y recopilar datos detallados de control de tiempo utilizando la línea de comandos del generador de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7b561e7d3be7bcbd3f71c81043e352482f0a04f6
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592474"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Procedimiento Instrumentar un servicio nativo y recopilar datos detallados de control de tiempo mediante la línea de comandos del generador de perfiles
En este artículo se describe cómo utilizar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar un servicio nativo (C/C++) y recopilar datos de control de tiempo detallados.  

> [!NOTE]
>  No puede generar perfiles de un servicio con el método de instrumentación si el servicio no se puede reiniciar después de iniciar el equipo, como por ejemplo un servicio que se inicia solamente cuando se inicia el sistema operativo.  
> 
>  Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.
 
 Para recopilar datos de control de tiempo detallados de un servicio nativo mediante el método de instrumentación, utilice la herramienta [VSInstr.exe](../profiling/vsinstr.md) para generar una versión instrumentada del componente. A continuación, reemplace la versión no instrumentada del servicio por la versión instrumentada, asegurándose de que el servicio se configura para iniciarse manualmente. A continuación, inicie el generador de perfiles.  

 Cuando se inicia el servicio, los datos de control de tiempo se recopilan automáticamente en un archivo de datos. Puede pausar y reanudar la recolección de datos durante la sesión de generación de perfiles.  

 Para finalizar una sesión de generación de perfiles, desactive el servicio y, a continuación, apague explícitamente el generador de perfiles.  

## <a name="start-the-application-with-the-profiler"></a>Iniciar la aplicación con el generador de perfiles  

#### <a name="to-start-profiling-a-native-service"></a>Para iniciar la generación de perfiles de un servicio nativo  

1. Abra una ventana de símbolo del sistema.  

2. Use la herramienta **VSInstr** para generar una versión instrumentada del archivo binario del servicio.  

3. Reemplace el archivo binario original por la versión instrumentada. En el Administrador de control de servicios de Windows, asegúrese de que el Tipo de inicio del servicio está establecido en Manual.  

4. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - La opción **/start:trace** inicia el generador de perfiles.  

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.*vsp*).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:trace**.  

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.  

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Especifica el número de segundos de espera para que el generador de perfiles se inicialice antes de que devuelva un error. Si no se especifica `Interval`, el generador de perfiles esperará indefinidamente. De manera predeterminada, **/start** termina inmediatamente. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Para iniciar el generador de perfiles con la recolección de datos en pausa, agregue la opción **/globaloff** a la línea de comandos **/start**. Utilice **/globalon** para reanudar la generación de perfiles. |
   | [/counter](../profiling/counter.md) **:** `Config` | Recopila información del contador de rendimiento del procesador especificado en Config. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente. |


5. Inicie el servicio en el Administrador de control de servicios.  

## <a name="control-data-collection"></a>Controlar la recopilación de datos  
 Cuando se está ejecutando el servicio, puede usar las opciones de *VSPerfCmd.exe* para iniciar y detener la escritura de datos en el archivo de datos del generador de perfiles. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de un servicio.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones de **VSPerfCmd** inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|  

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, detenga el servicio que está ejecutando el componente instrumentado y, después, llame a la opción [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1.  Detenga el servicio en el Administrador de control de servicios.  

2.  Cierre el generador de perfiles. Tipo:  

     **VSPerfCmd /shutdown**  

3.  Reemplace el módulo instrumentado con el original. Si es necesario, vuelva a configurar el Tipo de inicio del servicio.  

## <a name="see-also"></a>Vea también  
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)   
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)