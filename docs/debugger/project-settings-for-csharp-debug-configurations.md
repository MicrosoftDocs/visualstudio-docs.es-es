---
title: Configuración de proyectos para configuraciones de depuración de C# | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904067"
---
# <a name="project-settings-for--c-debug-configurations"></a>Configuración de proyectos para configuraciones de depuración en C#

Puede cambiar la configuración de depuración de los proyectos en C# en la [pestaña Depurar](#debug-tab) y la [pestaña Compilar](#build-tab) de las páginas de propiedades del proyecto.

Para abrir las páginas de propiedades, seleccione el proyecto en el **Explorador de soluciones** y, luego, elija el icono de **Propiedades** o haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

Para obtener más información, vea [Configuraciones Debug y Release](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Esta configuración no se aplica a las aplicaciones .NET Core, ASP.NET o para UWP. Para configurar las opciones de depuración de las aplicaciones para UWP, consulte [Iniciar una sesión de depuración para una aplicación de UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Ficha Depurar

|Parámetro|Descripción|
|-------------------------------------| - |
| **Configuración** | Establece el modo para compilar la aplicación. Seleccione **Active (Debug)** (Activo [depurar]), **Depurar**, **Liberar** o **Todas las configuraciones** en la lista desplegable. |
| **Acción de inicio** | Especifica la acción cuando se selecciona **Iniciar** en una configuración de depuración.<br />- **Proyecto de inicio** es el valor predeterminado y lanza el proyecto de inicio para la depuración. Para más información, consulte [Elegir el proyecto de inicio](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Programa externo de inicio** inicia y asocia a una aplicación que no forma parte de un proyecto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para más información, consulte [Asociar con procesos en ejecución con el depurador](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Iniciar explorador con la dirección URL** le permite depurar una aplicación web. |
| **Opciones de inicio** > **Argumentos de la línea de comandos** | Especifica los argumentos de la línea de comandos de la aplicación que se va a depurar. El nombre de comando es el nombre de la aplicación especificado en **Programa externo de inicio**. |
| **Opciones de inicio** > **Directorio de trabajo** | Especifica el directorio de trabajo de la aplicación que se depura. En C# , el directorio de trabajo es *\bin\debug* de forma predeterminada.
| **Opciones de inicio** > **Usar máquina remota**|Para la depuración remota, seleccione esta opción y escriba el nombre del destino de depuración remota o un [nombre de servidor de msvsmon](../debugger/remote-debugging.md). <br />La ubicación de una aplicación en la maquina remota se especifica mediante la propiedad **Ruta de acceso de resultados**, en la pestaña **Compilar**. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.
| **Motor de depuración** > **Habilitar depuración de código no administrado** | Depura las llamadas a código Win32 nativo (no administrado) desde la aplicación administrada. |
| **Motor de depuración** > **Habilitar depuración de SQL Server** | Depura los objetos de base de datos de SQL Server. |

## <a name="build-tab"></a>Pestaña Compilar

|Parámetro|Descripción|
|-------------|-----------------|
|**General** > **Símbolos de compilación condicional**|Define las constantes DEBUG y TRACE si se selecciona.<br /><br /> Estas constantes permiten la compilación condicional de [Debug (clase)](/dotnet/api/system.diagnostics.debug) y [Trace (clase)](/dotnet/api/system.diagnostics.trace). Con la definición de estas constantes, los métodos de clase Debug y Trace generan resultados en la [ventana Salida](../ide/reference/output-window.md). Sin estas constantes, los métodos de clase Debug y Trace no se compilan y no se generan resultados.<br /><br />Normalmente, DEBUG se define en la versión de depuración de una compilación y no se define en la versión de lanzamiento. TRACE se define en las versiones de lanzamiento y de depuración.|
|**General** > **Optimizar código**|A menos que un error aparezca solo en el código optimizado, deje esta opción desactivada para las compilaciones de depuración. El código optimizado es más difícil de depurar, puesto que las instrucciones no se corresponden directamente con las instrucciones del código fuente.|
|**Salida** > **Ruta de acceso de resultados**|Normalmente se establece en *bin\Debug* para la depuración.|
|Botón **Opciones avanzadas**|Para información sobre las opciones de depuración avanzadas, consulte [Cuadro de diálogo Configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). El formato portable para los archivos de símbolos ( *.pdb*) es un formato multiplataforma reciente para las aplicaciones .NET Core.

## <a name="see-also"></a>Vea también
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)