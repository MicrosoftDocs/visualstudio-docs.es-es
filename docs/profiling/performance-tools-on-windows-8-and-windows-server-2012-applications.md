---
title: Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69b817af15b782ebd1e281d51855d62b11e8f470
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262952"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012

Las características de seguridad mejoradas a partir de Windows 8 y Windows Server 2012 han requerido cambios significativos en la forma en que las herramientas de rendimiento de Visual Studio recopilan datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. En este tema se describen los cambios para las herramientas de rendimiento a partir de las plataformas Windows 8 y Windows Server 2012.

> [!NOTE]
> Las herramientas de rendimiento en otras versiones compatibles de Windows (Windows 7, Windows Server 2008 R2) no han cambiado.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Recopilar datos de aplicaciones para UWP desde el IDE de Visual Studio

Cuando se generan perfiles de una aplicación para UWP escrita en JavaScript y HTML 5, se recopilan datos de instrumentación para el código JavaScript. Cuando se generan perfiles de una aplicación para UWP o componente escrito en Visual C++, Visual C# o Visual Basic, se recopilan datos de muestreo para el código nativo y administrado. Se pueden generar perfiles de la aplicación localmente o en un equipo remoto.

Estas características y opciones de generación de perfiles no se admiten al generar perfiles de las aplicaciones para UWP:

- Generación de perfiles de aplicaciones JavaScript usando el método de muestreo.
- Generación de perfiles de código administrado y nativo usando el método de instrumentación.
- Generación de perfiles de simultaneidad
- Generación de perfiles de memoria .NET
- Generación de perfiles de interacción de capas (TIP)
- Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.
- Opciones de instrumentación, como recopilar datos del contador de rendimiento y de Windows, o especificar opciones de la línea de comandos adicionales.

Para más información sobre cómo generar perfiles de aplicaciones para UWP, consulte los artículos siguientes:

- [Ejecución de aplicaciones para UWP en el equipo local](/visualstudio/debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml)
- [Ejecución de aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Primer vistazo a la generación de perfiles](profiling-feature-tour.md)
- [Memoria de JavaScript](../profiling/javascript-memory.md)
- [Generar perfiles de código de Visual C++, Visual C# y Visual Basic en aplicaciones para UWP en un equipo local](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Generar perfiles de código de Visual C++, Visual C# y Visual Basic en aplicaciones para UWP en un dispositivo remoto](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analizar datos de rendimiento de código de Visual C++, Visual C# y Visual Basic en aplicaciones para UWP](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Recopilar datos de aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012 desde el IDE de Visual Studio

La generación de perfiles mediante el método de instrumentación no ha cambiado para Windows 8.

La generación de perfiles de interacción de capas (TIP) no se admite al usar el método de muestreo.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Recopilar datos de aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012 mediante el muestreo desde el IDE de Visual Studio

Estas características y opciones de generación de perfiles no se admiten al generar perfiles de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012 usando el método de muestreo:

- Generación de perfiles de interacción de capas (TIP). La recopilación de datos de TIP se admite mediante la instrumentación.

- Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.

## <a name="profile-from-the-command-line"></a>Generar perfiles desde la línea de comandos

Para recopilar datos de generación de perfiles en dispositivos con Windows 8 y Windows Server 2012, incluidos los dispositivos que no tienen una instalación de Visual Studio, se usan dos herramientas de línea de comandos:

|Nombre de herramienta.|Descripción|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Recopila datos de generación de perfiles de aplicaciones para UWP y datos de generación de perfiles de ejemplo de aplicaciones de escritorio de Windows 8 y de Windows Server 2012.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Recopila datos de generación de perfiles de instrumentación, simultaneidad e interacción de capas de las aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012. Recopila todos los tipos de datos de generación de perfiles de las versiones anteriores de Windows.|

Ambas herramientas se instalan con Visual Studio para usarse en el equipo local.

Para generar perfiles de aplicaciones en dispositivos que no tienen Visual Studio instalado, realice alguno de los siguientes procedimientos:

- Descargue las herramientas como parte de las Herramientas remotas para Visual Studio desde el [sitio web de MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).

- Copie y ejecute el programa de instalación independiente de las herramientas de generación de perfiles desde el equipo de Visual Studio. Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Elija el programa de instalación para el sistema operativo (x86/x64) del equipo remoto.

> [!NOTE]
> Para recopilar datos de generación de perfiles TIP, debe instalar el generador de perfiles independiente del equipo de Visual Studio en el equipo remoto.

Estas características y opciones de generación de perfiles no se admiten al generar perfiles de aplicaciones de Windows 8 y Windows Server 2012 desde la línea de comandos:

- Recopilación de datos de aplicaciones web de Windows 8 y Windows Server 2012 usando el modo de muestreo con [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Recopilación de datos de muestreo usando VsPerfCmd.exe.

- Opciones de muestreo, como establecer el intervalo de tiempo y el evento de muestreo, o recopilar datos adicionales del contador de rendimiento.

## <a name="collect-tier-interaction-tip-data"></a>Recopilar datos de interacciones de capas (TIP)

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de ADO.NET. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.

**Ediciones de Visual Studio**

Los datos de generación de perfiles de interacción de capas se pueden recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.

**Windows 8 y Windows Server 2012**

1. Para recopilar datos de interacción de capas de aplicaciones que se ejecutan en el escritorio de Windows 8 o en Windows Server 2012, debe usar el método de instrumentación.

2. No se pueden recopilar datos de interacción de capas para las aplicaciones para UWP.

3. Puede incluir datos de interacción de capas en todos los métodos de generación de perfiles de otras versiones compatibles de Windows.

**Asistente para rendimiento y Explorador de rendimiento**

Debe agregar la opción de recopilación de datos de interacción de capas a una ejecución de generación de perfiles desde el Explorador de rendimiento. También debe agregar el proyecto, el archivo ejecutable o el sitio web al nodo de destino del Explorador de rendimiento. Vea [Recopilación de datos de interacción de capas](../profiling/collecting-tier-interaction-data.md).

**Recopilación de datos de TIP en un equipo remoto**

Para recopilar datos de interacción de capas en un equipo remoto, debe copiar el archivo **vs\_profiler\_** _\<plataforma>_ **\_** _\<lenguaje>_ **.exe** de la carpeta *%VSInstallDir%\Team Tools\Performance Tools\Setups* de un equipo de Visual Studio en el equipo remoto e instalarlo. Las herramientas de generación de perfiles no se pueden usar en el paquete de descarga de [Depuración remota](../debugger/remote-debugging.md) .

Puede usar [VSPerfCmd](../profiling/vsperfcmd.md) o [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) para recopilar los datos de generación de perfiles.

**Informes TIP**

Los datos de interacción de capas solo se pueden ver en Visual Studio Enterprise. Los informes de interacción de capas basados en archivos no están disponibles en [VSPerfReport](../profiling/vsperfreport.md) .

## <a name="see-also"></a>Vea también

[Explorador de rendimiento](../profiling/performance-explorer.md)
[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[Generar perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)