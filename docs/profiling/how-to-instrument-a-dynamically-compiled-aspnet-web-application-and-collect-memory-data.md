---
title: Procedimiento Instrumentar una aplicación web ASP.NET compilada dinámicamente y recopilar datos de memoria mediante la línea de comandos del generador de perfiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: da1c1ad76802496108284dcb6fc037bfd7443180
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940919"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedimiento Instrumentar una aplicación web ASP.NET compilada dinámicamente y recopilar datos de memoria mediante la línea de comandos del generador de perfiles
En este tema se explica cómo usar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para recopilar datos detallados de asignación de memoria y de duración de objetos de .NET para una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilada dinámicamente mediante el método de generación de perfiles de instrumentación.  

> [!NOTE]
>  Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.
 
 Para recopilar datos de rendimiento de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe modificar el archivo *web.config* de la aplicación de destino para permitir que la herramienta [VSInstr.exe](../profiling/vsinstr.md) instrumente los archivos de aplicación compilados dinámicamente. Luego use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para configurar el servidor que hospeda la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y habilite la generación de perfiles de memoria de .NET mediante el establecimiento de las variables de entorno adecuadas; por último, reinicie el equipo.  

 Para recopilar datos, inicie el generador de perfiles y luego ejecute la aplicación de destino. Mientras el generador de perfiles está asociado a la aplicación, puede detener y reanudar la recopilación de datos. Una vez recopilados los datos adecuados, cierre la aplicación, cierre el proceso de trabajo de Internet Information Services (IIS) y luego apague el generador de perfiles.  

 Cuando haya completado el trabajo de generación de perfiles, restaure el archivo *web.config* y el servidor web a su estado original.  

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Configurar la aplicación web ASP.NET y el servidor web  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Para configurar la aplicación web ASP.NET y el servidor web  

1.  Modifique el archivo *web.config* de la aplicación de destino. Vea [Cómo: Modificar archivos Web.config para instrumentar y generar perfiles de aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).  

2.  Abra una ventana del símbolo del sistema en el equipo que hospeda la aplicación web.  

3.  Inicialice las variables del entorno de generación de perfiles. Tipo:  

     **VSPerfClrEnv /globaltracegc**  

     o bien  

     **VSPerfClrEnv /globaltracegclife**  

    -   **/globaltracegc** habilita la recopilación de datos de asignación de memoria.  

    -   **/globaltracegclife** habilita la recopilación tanto de datos de asignación de memoria como de datos de duración de objetos.  

4.  Reinicie el equipo.  

## <a name="run-the-profiling-session"></a>Ejecutar la sesión de generación de perfiles  

#### <a name="to-profile-the-aspnet-web-application"></a>Para generar el perfil de la aplicación web ASP.NET  

1. Inicie el generador de perfiles. Tipo:  

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - La opción **/start:trace** inicia el generador de perfiles.  

   - La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.*vsp*).  

     Puede usar cualquiera de las siguientes opciones con la opción **/start:trace**.  

   > [!NOTE]
   >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.  

   | Opción | Descripción |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Especifica el dominio opcional y el nombre de usuario de la cuenta propietaria del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El nombre aparece en la columna **Nombre de usuario** de la pestaña **Procesos** del Administrador de tareas de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Habilita la generación de perfiles de procesos en otras sesiones. Esta opción es necesaria si la aplicación se ejecuta en una sesión diferente. El identificador de sesión se muestra en la columna **Id. de sesión** de la pestaña **Procesos** del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Inicia el generador de perfiles con la recolección de datos en pausa. Utilice [/globalon](../profiling/globalon-and-globaloff.md) para reanudar la generación de perfiles. |
   | [/counter](../profiling/counter.md) **:** `Config` | Recopila información del contador de rendimiento del procesador especificado en `Config`. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo *.etl* independiente. |


2. Inicie la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de la manera habitual.  

## <a name="control-data-collection"></a>Controlar la recopilación de datos  
 Durante la ejecución de la aplicación de destino, puede controlar la recopilación de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

-   Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|  

-   También puede utilizar la opción [/mark](../profiling/mark.md) de **VSPerfCmd.exe** para insertar una marca de generación de perfiles en el archivo de datos. El comando **/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario. Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles.  

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de destino, detenga Internet Information Services (IIS) para detener el proceso de generación de perfiles y, luego, apague el generador de perfiles. Por último, reinicie IIS.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1. Cierre la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  

2. Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] restableciendo Internet Information Services (IIS). Tipo:  

    **IISReset /stop**  

3. Cierre el generador de perfiles. Tipo:  

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)  

4. Reinicie IIS. Tipo:  

    **IISReset /start**  

## <a name="restore-the-application-and-computer-configuration"></a>Restaurar la configuración del equipo y la aplicación  
 Después de completar la generación de perfiles, reemplace el archivo *web.config*, borre las variables de entorno de generación de perfiles y reinicie el equipo para restaurar el servidor y la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a sus estados originales.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Para restaurar la configuración del equipo y la aplicación  

1.  Reemplace el archivo *web.config* por una copia del archivo original.  

2.  (Opcional). Borre las variables del entorno de generación de perfiles. Tipo:  

     **VSPerfCmd /globaloff**  

3.  Reinicie el equipo.  

## <a name="see-also"></a>Vea también  
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)
