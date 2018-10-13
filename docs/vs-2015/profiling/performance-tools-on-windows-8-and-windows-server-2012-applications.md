---
title: Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e495f5f07e5db2214c7eca8bc2c21df253fa49e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195525"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que las herramientas de rendimiento de Visual Studio recopilan datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. En este tema se describen los cambios para las herramientas de rendimiento en las plataformas Windows 8 y Windows Server 2012.  
  
> [!NOTE]
>  Las herramientas de rendimiento en otras versiones compatibles de Windows (Windows 7, Windows Server 2008 R2) no han cambiado.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Recopilar datos de aplicaciones de la Tienda Windows desde el IDE de Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Recopilar datos de aplicaciones que se ejecutan en el escritorio Windows 8 o en Windows Server 2012 desde el IDE de Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
-   [Recopilar datos de aplicaciones que se ejecutan en el escritorio Windows 8 o en Windows Server 2012 mediante el muestreo desde el IDE de Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
 [Generación de perfiles desde la línea de comandos](#BKMK_Profiling_from_the_command_line)  
  
 [Recopilar datos de interacciones de capas (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Recopilar datos de aplicaciones de la Tienda Windows desde el IDE de Visual Studio  
 Cuando se generan perfiles de una aplicación de la Tienda Windows escrita en JavaScript y HTML 5, se recopilan datos de instrumentación para el código JavaScript. Cuando se generan perfiles de una aplicación o componente de la Tienda Windows escrita en Visual C++, Visual C# o Visual Basic, se recopilan datos de muestreo para el código nativo y administrado. Se pueden generar perfiles de la aplicación localmente o en un equipo remoto.  
  
 Estas características y opciones de generación de perfiles no se admiten al generar perfiles de las aplicaciones de la Tienda Windows:  
  
-   Generación de perfiles de aplicaciones JavaScript usando el método de muestreo.  
  
-   Generación de perfiles de código administrado y nativo usando el método de instrumentación.  
  
-   Generación de perfiles de simultaneidad  
  
-   Generación de perfiles de memoria .NET  
  
-   Generación de perfiles de interacción de capas (TIP)  
  
-   Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.  
  
-   Opciones de instrumentación, como recopilar datos del contador de rendimiento y de Windows, o especificar opciones de la línea de comandos adicionales.  
  
 Para obtener más información sobre cómo generar perfiles de aplicaciones de la Tienda Windows, consulte los temas siguientes en el Centro de desarrollo de Windows:  
  
 [Ejecutar aplicaciones de la Tienda Windows en la máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
 [Ejecutar aplicaciones de la Tienda Windows en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
 [Analizar el rendimiento de la aplicación](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
-   [Tiempo de función de JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
-   [Tiempo de función de JavaScript en un dispositivo remoto](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
-   [Analizar datos de tiempo de función de JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
-   [Generar perfiles de código de Visual C++, Visual C# y Visual Basic en aplicaciones de la Tienda Windows en un equipo local](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
-   [Generar perfiles de código de Visual C++, Visual C# y Visual Basic en aplicaciones de la Tienda Windows en un equipo remoto](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
-   [Analizar datos de rendimiento de código de Visual C++, Visual C# y Visual Basic en aplicaciones de la Tienda Windows](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Recopilar datos de aplicaciones que se ejecutan en el escritorio Windows 8 o en Windows Server 2012 desde el IDE de Visual Studio  
 La generación de perfiles mediante el método de instrumentación no ha cambiado para Windows 8.  
  
 La generación de perfiles de interacción de capas (TIP) no se admite al usar el método de muestreo.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Recopilar datos de aplicaciones que se ejecutan en el escritorio Windows 8 o en Windows Server 2012 mediante el muestreo desde el IDE de Visual Studio  
 Estas características y opciones de generación de perfiles no se admiten al generar perfiles de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012 usando el método de muestreo:  
  
-   Generación de perfiles de interacción de capas (TIP). La recopilación de datos de TIP se admite mediante la instrumentación.  
  
-   Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Generación de perfiles desde la línea de comandos  
 Para recopilar datos de generación de perfiles en dispositivos con Windows 8 y Windows Server 2012, incluidos los dispositivos que no tienen una instalación de Visual Studio, se usan dos herramientas de línea de comandos:  
  
|Nombre de herramienta.|Descripción|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Recopila datos de generación de perfiles de aplicaciones de la Tienda Windows y datos de generación de perfiles de ejemplo de aplicaciones de escritorio de Windows 8 y aplicaciones de Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Recopila datos de generación de perfiles de instrumentación, simultaneidad e interacción de capas de las aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012. Recopila todos los tipos de datos de generación de perfiles de las versiones anteriores de Windows.|  
  
 Ambas herramientas se instalan con Visual Studio para usarse en el equipo local.  
  
 Para generar perfiles de aplicaciones en dispositivos que no tienen Visual Studio instalado, realice alguno de los siguientes procedimientos:  
  
-   Descargue las herramientas como parte de las Herramientas remotas para Visual Studio desde el [sitio web de MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Copie y ejecute el programa de instalación independiente de las herramientas de generación de perfiles desde el equipo de Visual Studio. Los programas de instalación están en la carpeta *%VSInstallDir%* **\Team Tools\Performance Tools\Setups** . Elija el programa de instalación para el sistema operativo (x86/x64) del equipo remoto.  
  
> [!NOTE]
>  Para recopilar datos de generación de perfiles TIP, debe instalar el generador de perfiles independiente del equipo de Visual Studio en el equipo remoto.  
  
 Estas características y opciones de generación de perfiles no se admiten al generar perfiles de aplicaciones de Windows 8 y Windows Server 2012 desde la línea de comandos:  
  
-   Recopilación de datos de aplicaciones web de Windows 8 y Windows Server 2012 usando el modo de muestreo con [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   Recopilación de datos de muestreo usando VsPerfCmd.exe.  
  
-   Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Recopilar datos de interacciones de capas (TIP)  
 La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de ADO.NET. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  
  
 **Ediciones de Visual Studio**  
  
 Los datos de generación de perfiles de interacción de capas se pueden recopilar usando [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]o [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] y [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 y Windows Server 2012**  
  
1.  Para recopilar datos de interacción de capas de aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012, debe usar el método de instrumentación.  
  
2.  No se pueden recopilar datos de interacción de capas para las aplicaciones de la Tienda Windows.  
  
3.  Puede incluir datos de interacción de capas en todos los métodos de generación de perfiles de otras versiones compatibles de Windows.  
  
 **Asistente para rendimiento y Explorador de rendimiento**  
  
 Debe agregar la opción de recopilación de datos de interacción de capas a una ejecución de generación de perfiles desde el Explorador de rendimiento. También debe agregar el proyecto, el archivo ejecutable o el sitio web al nodo de destino del Explorador de rendimiento. Consulte [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md).  
  
 **Recopilación de datos de TIP en un equipo remoto**  
  
 Para recopilar datos de interacción de capas en un equipo remoto, debe copiar el **vs\_profiler\_**_\<plataforma >_ **\_**  _\<Lenguaje >_**.exe** de archivos desde el _% VSInstallDir %_**\Team Tools\Performance Tools\Setups**carpeta de Visual Studio del equipo en el equipo remoto e instalarlo. Las herramientas de generación de perfiles no se pueden usar en el paquete de descarga de [Herramientas remotas para Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
 Puede usar [VSPerfCmd](../profiling/vsperfcmd.md) o [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) para recopilar los datos de generación de perfiles.  
  
 **Informes TIP**  
  
 Los datos de interacción de capas solo se pueden ver en el IDE de [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . Los informes de interacción de capas basados en archivos no están disponibles en [VSPerfReport](../profiling/vsperfreport.md) .  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)   
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)



