---
title: VSPerf | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 830aa028e8c34beb5fd6818c40ffcfc7f3fa461b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755255"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilice la herramienta de línea de comandos **VsPerf** para:  
  
1. Generar perfiles de aplicaciones de la Tienda Windows desde la línea de comandos cuando Visual Studio no esté instalado en el dispositivo.  
  
2. Generar perfiles de aplicaciones de escritorio de Windows 8 y aplicaciones de Windows Server 2012 mediante el método de generación de perfiles de muestreo.  
  
   Para obtener más información acerca de las opciones de generación de perfiles, consulte [Herramientas de rendimiento en Windows 8 y aplicaciones de Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 Este tema describe las opciones que puede usar con la herramienta de línea de comandos `vsperf.exe`. El tema contiene las siguientes secciones:  
  
 [Solo aplicaciones de la Tienda Windows](#BKMK_windows_store_apps_only)  
  
 [Aplicaciones de escritorio de Windows 8 y las aplicaciones de Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Todas las aplicaciones](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Solo aplicaciones de la Tienda Windows  
 Estas opciones se aplican solo a las aplicaciones de la Tienda Windows.  
  
|||  
|-|-|  
|**/app:{AppName}**|Inicia el generador de perfiles y espera a que la aplicación especificada se ejecute desde el menú Inicio.<br /><br /> Ejecute `vsperf /listapps` para ver el nombre de la aplicación y PackageFullName de las aplicaciones instaladas.|  
|**/package:{PackageFullName}**|Inicia el generador de perfiles y espera a que la aplicación especificada se ejecute desde el menú Inicio.<br /><br /> Ejecute `vsperf /listapps` para ver el nombre de la aplicación y PackageFullName de las aplicaciones instaladas.|  
|**/js**|Se requiere para generar perfiles de aplicaciones de JavaScript.<br /><br /> Recopilar datos de rendimiento de aplicaciones de JavaScript.<br /><br /> Utilícelo solo con/package o /attach.|  
|**/noclr**|Opcional. No se recopilan datos de CLR.<br /><br /> Utilícelo solo con/package o /attach.<br /><br /> Optimización, no se resolverán símbolos administrados.|  
|**/listapps**|Lista los nombres y PackageFullNames de la aplicación instalada.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Aplicaciones de escritorio de Windows 8 y las aplicaciones de Windows Server 2012  
 Estas opciones no funcionan en aplicaciones de la Tienda Windows.  
  
|||  
|-|-|  
|**/launch:{Executable}**|Inicia el archivo ejecutable especificado y comienza la generación de perfiles.|  
|**/args:{ExecutableArguments}**|Especifica los argumentos de línea de comandos para pasar el destino de **/launch**.|  
|**/console**|Ejecuta el destino de **/launch** en una nueva ventana de comandos.|  
  
##  <a name="BKMK_All_applications"></a> Todas las aplicaciones  
 Estas opciones se aplican a cualquier aplicación de Windows 8 o de Windows Server 2012.  
  
|||  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Recopila datos de los procesos especificados.<br /><br /> Utilice el Administrador de tareas para ver el identificador de proceso (PID) y el nombre de proceso de aplicaciones en ejecución.|  
|**/file:{ReportName}**|Opcional. Especifica el archivo de salida (sobrescribe el archivo existente).<br /><br /> Utilícelo solo con/package o /attach.|  
|**/pause**|Pausa la recopilación de datos.|  
|**/resume**|Reanuda la recopilación de datos.|  
|**/stop**|Detiene la recopilación de datos y finaliza los procesos de destino.|  
|**/detach**|Detiene la recopilación de datos, pero permite que los procesos de destino sigan ejecutándose.|  
|**/status**|Muestra el estado del generador de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)



