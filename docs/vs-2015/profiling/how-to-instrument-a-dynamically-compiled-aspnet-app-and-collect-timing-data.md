---
title: Instrumentación de una aplicación web ASP.NET compilada dinámicamente y recopilación de datos detallados de control de tiempo con el generador de perfiles mediante la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c140ae2-ecdd-48c7-bd89-3dc1b88e19b0
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e815170640b57a667b71aac3e9e3526e2fe8b275
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592525"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Cómo: Instrumentar una aplicación web ASP.NET compilada dinámicamente y recopilar datos detallados de control de tiempo con el generador de perfiles utilizando la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: Instrumentar una aplicación de Web ASP.NET dinámicamente compilado y recopilar datos detallados de control de tiempo con el Profiler mediante el uso de la línea de comandos](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line).  
  
En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para recopilar datos detallados de control de tiempo acerca de una aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] compilada dinámicamente utilizando el método de generación de perfiles mediante instrumentación.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para recopilar datos de rendimiento de una aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], debe modificar el archivo web.config de la aplicación de destino para permitir que la herramienta [VSInstr.exe](../profiling/vsinstr.md) instrumente los archivos de aplicación compilados dinámicamente. A continuación, use la herramienta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para establecer las variables de entorno adecuadas en el servidor web que habiliten la generación de perfiles y, después, reinicie el equipo.  
  
 Inicie el generador de perfiles y, a continuación, ejecute la aplicación de destino. Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Al terminar de generar perfiles, cierre la aplicación, cierre el proceso de trabajo de Internet Information Services (IIS) y, a continuación, cierre el generador de perfiles. Cuando haya completado el trabajo de generación de perfiles, restaure el archivo web.config y el servidor web a su estado original.  
  
## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Configuración de la aplicación Web ASP.NET y el servidor web  
  
#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Para configurar la aplicación web ASP.NET y el servidor web  
  
1.  Modifique el archivo web.config de la aplicación de destino. Vea [Cómo: Modificar archivos web.config para instrumentar y generar perfiles de aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  
  
2.  Abra una ventana de símbolo del sistema.  
  
3.  Inicialice las variables del entorno de generación de perfiles. Tipo:  
  
     **VSPerfClrEnv /globaltraceon**  
  
    -   **/globaltraceon** habilita la generación de perfiles con el método de instrumentación.  
  
4.  Reinicie el equipo.  
  
## <a name="running-the-profiling-session"></a>Ejecución de la sesión de generación de perfiles  
  
#### <a name="to-profile-the-web-application"></a>Para generar perfiles de la aplicación web  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Inicie el generador de perfiles. Tipo:  
  
     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   La opción **/start:trace** inicia el generador de perfiles.  
  
    -   La opción **/output:**`OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  
  
     Puede usar cualquiera de las siguientes opciones con la opción **/start:trace**.  
  
    > [!NOTE]
    >  Normalmente, las opciones **/user** y **/crosssession** son necesarias para aplicaciones ASP.NET.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso de trabajo de ASP.NET. Esta opción es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició la sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión. Esta opción es necesaria si la aplicación ASP.NET se ejecuta en otra sesión. El identificador de sesión se muestra en la columna Id. de sesión de la pestaña Procesos del Administrador de tareas de Windows. **/CS** se puede especificar como una abreviatura de **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Inicia el generador de perfiles con la recolección de datos en pausa. Utilice [/globalon](../profiling/globalon-and-globaloff.md) para reanudar la generación de perfiles.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Recopila información del contador de rendimiento del procesador especificado en `Config`. La información del contador se agrega a los datos recopilados en cada evento de generación de perfiles.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|  
  
3.  Inicie la aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de la manera habitual.  
  
## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Durante la ejecución de la aplicación de destino, puede controlar la recopilación de datos iniciando o deteniendo la escritura de los datos en un archivo de datos del generador de perfiles mediante el uso de las opciones de **VSPerfCmd.exe**. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  
  
-   Los siguientes pares de opciones inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso especificado por el identificador de proceso (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Inicia (**/threadon**) o detiene (**/threadoff**) la recopilación de datos para el subproceso especificado por el identificador de subproceso (`TID`).|  
  
-   También puede utilizar la opción [/mark](../profiling/mark.md) de **VSPerfCmd.exe** para insertar una marca de generación de perfiles en el archivo de datos. El comando **/mark** agrega un identificador, una marca de tiempo y una cadena de texto opcional definida por el usuario. Las marcas se pueden utilizar para filtrar los datos que se muestran en las vistas de informes y datos del generador de perfiles.  
  
## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar una sesión de generación de perfiles, cierre la aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de destino, restablezca IIS para detener el proceso perfilado y, a continuación, apague el generador de perfiles.  
  
#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  
  
1.  Cierre la aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Cierre el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] restableciendo Internet Information Services (IIS). Tipo:  
  
     **IISReset /stop**  
  
3.  Cierre el generador de perfiles. Tipo:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
4.  Reinicie IIS. Tipo:  
  
     **IISReset /start**  
  
## <a name="restoring-the-application-and-computer-configuration"></a>Restauración de la configuración del equipo y la aplicación  
 Después de completar la generación de perfiles, reemplace el archivo web.config, borre las variables de entorno de generación de perfiles y reinicie el equipo para restaurar la aplicación y el servidor a los estados anteriores a la generación de perfiles.  
  
#### <a name="to-restore-the-application-and-computer-configuration"></a>Para restaurar la configuración del equipo y la aplicación  
  
1.  Reemplace el archivo web.config por una copia del archivo original.  
  
2.  Borre las variables del entorno de generación de perfiles. Tipo:  
  
     **VSPerfCmd /globaloff**  
  
3.  Reinicie el equipo.  
  
## <a name="see-also"></a>Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)



