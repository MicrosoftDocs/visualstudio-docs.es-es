---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilice la herramienta de línea de comandos **VsPerf** para:  
  
1.  El perfil Windows almacena aplicaciones de línea de comandos cuando Visual Studio no está instalado en el dispositivo.  
  
2.  Generar perfiles de aplicaciones de escritorio Windows 8 y aplicaciones Windows Server 2012 utilizando el método de generación de perfiles de muestreo.  
  
 Para obtener más información sobre las opciones de generación de perfiles, consulte [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 Este tema describe las opciones que se pueden utilizar con la herramienta de línea de comandos `vsperf.exe`.  Este tema contiene las siguientes secciones:  
  
 [Aplicaciones de almacén de Windows sólo](#BKMK_windows_store_apps_only)  
  
 [Sólo aplicaciones de escritorio Windows 8 y Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Todas las aplicaciones](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Aplicaciones de almacén de Windows sólo  
 Estas opciones se aplican solo a las aplicaciones de almacén de Windows.  
  
|||  
|-|-|  
|**\/app:{AppName}**|Se inicia el generador de perfiles y se espera a la aplicación especificada que se iniciará desde el menú Inicio.<br /><br /> Ejecute `vsperf /listapps` para ver el nombre de la aplicación y el PackageFullName de las aplicaciones instaladas.|  
|**\/package:{PackageFullName}**|Se inicia el generador de perfiles y se espera a la aplicación especificada que se iniciará desde el menú Inicio.<br /><br /> Ejecute `vsperf /listapps` para ver el nombre de la aplicación y el PackageFullName de las aplicaciones instaladas.|  
|**\/js**|Requerido para generar perfiles de aplicaciones de JavaScript.<br /><br /> Recopilar datos de rendimiento de aplicaciones de JavaScript.<br /><br /> Úselo exclusivamente con \/paquete o \/adjuntar.|  
|**\/noclr**|Opcional.  No recopile datos CLR.<br /><br /> Úselo exclusivamente con \/paquete o \/adjuntar.<br /><br /> Optimización, no se resolverán símbolos administrados.|  
|**\/listapps**|Listar nombres de aplicaciones instaladas y PackageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Sólo aplicaciones de escritorio Windows 8 y Windows Server 2012  
 Estas opciones no funcionan en aplicaciones de almacén de Windows.  
  
|||  
|-|-|  
|**\/launch:{Executable}**|Inicia y comienza la generación de perfiles del archivo ejecutable especificado.|  
|**\/args:{ExecutableArguments}**|Especifica los argumentos de la línea de comandos para pasar el destino **\/launch**.|  
|**\/console**|Ejecuta el destino **\/launch** en una nueva ventana de comandos.|  
  
##  <a name="BKMK_All_applications"></a> Todas las aplicaciones  
 Esta opción se aplica a cualquier aplicación de Windows 8 o Windows Server 2012.  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|Recopila los datos de los procesos especificados.<br /><br /> Utilice el Administrador de tareas para ver los nombres del identificador de procesos \(PID\) y del proceso de las aplicaciones en ejecución.|  
|**\/file:{ReportName}**|Opcional.  Especifica el archivo de salida \(sobrescribe el archivo existente\).<br /><br /> Úselo exclusivamente con \/paquete o \/adjuntar.|  
|**\/pause**|Pausar recolección de datos.|  
|**\/resume**|Reanudar recolección de datos .|  
|**\/stop**|Detener la recopilación de datos y terminar los procesos de destino.|  
|**\/detach**|Detener la recopilación de datos, pero dejando que los procesos de destino continúen ejecutándose.|  
|**\/status**|Mostrar el estado del generador de perfiles.|  
  
## Vea también  
 [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)