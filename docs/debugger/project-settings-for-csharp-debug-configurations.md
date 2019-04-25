---
title: Configuración de proyectos para una C# depurar config | Microsoft Docs
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
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680612"
---
# <a name="project-settings-for--c-debug-configurations"></a>Configuración de proyectos para configuraciones de depuración en C#

Puede cambiar C# configuración de depuración en proyectos el [ficha Depurar](#debug-tab) y [pestaña compilación](#build-tab) de las páginas de propiedades del proyecto.

Para abrir las páginas de propiedades, seleccione el proyecto en **el Explorador de soluciones** y, a continuación, seleccione el **propiedades** icono, o haga clic en el proyecto y seleccione **propiedades**.

Para obtener más información, vea [Configuraciones Debug y Release](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Esta configuración no se aplica a las aplicaciones de .NET Core, ASP.NET o UWP. Para configurar las opciones de depuración para aplicaciones UWP, consulte [iniciar una sesión de depuración para una aplicación UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Ficha Depurar

|Parámetro|Descripción|
|-------------------------------------| - |
| **Configuración** | Establece el modo para crear la aplicación. Seleccione **activo (depurar)**, **depurar**, **versión**, o **todas las configuraciones de** en la lista desplegable. |
| **Acción de inicio** | Especifica la acción cuando se selecciona **iniciar** en una configuración de depuración.<br />- **Proyecto de inicio** es el valor predeterminado y lanza el proyecto de inicio para la depuración. Para obtener más información, consulte [elegir el proyecto de inicio](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Iniciar programa externo** inicia y se asocia a una aplicación que no es parte de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Para obtener más información, consulte [adjuntar a procesos en ejecución con el depurador](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Iniciar explorador con la dirección URL** le permite depurar una aplicación web. |
| **Opciones de inicio** > **argumentos de línea de comandos** | Especifica los argumentos de línea de comandos para la aplicación que se está depurando. El nombre del comando es el nombre de aplicación especificado en **iniciar programa externo**. |
| **Opciones de inicio** > **directorio de trabajo** | Especifica el directorio de trabajo de la aplicación que se está depurando. En C#, el directorio de trabajo es *\bin\debug* de forma predeterminada.
| **Opciones de inicio** > **usar equipo remoto**|Para la depuración remota, seleccione esta opción y escriba el nombre del destino de depuración remoto, o un [nombre de servidor Msvsmon](../debugger/remote-debugging.md). <br />La ubicación de una aplicación en el equipo remoto especificada por el **ruta de acceso de salida** propiedad en el **compilar** ficha. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.
| **Motor de depuración** > **habilitar la depuración de código no administrado** | Depura las llamadas a código nativo de Win32 (no administrado) desde la aplicación administrada. |
| **Motor de depuración** > **depuración habilitar SQL Server** | Depura los objetos de base de datos de SQL Server. |

## <a name="build-tab"></a>Pestaña Compilar

|Parámetro|Descripción|
|-------------|-----------------|
|**General** > **símbolos de compilación condicional**|Defina las constantes DEBUG y TRACE si ha seleccionado.<br /><br /> Estas constantes permiten la compilación condicional de [Debug (clase)](/dotnet/api/system.diagnostics.debug) y [Trace (clase)](/dotnet/api/system.diagnostics.trace). Con la definición de estas constantes, los métodos de clase Debug y Trace generan resultados en la [ventana Salida](../ide/reference/output-window.md). Sin estas constantes, los métodos de clase Debug y Trace no se compilan y no se generan resultados.<br /><br />Por lo general, depuración se define en la versión de depuración de una compilación y no definida en la versión de lanzamiento. TRACE se define en las versiones de depuración y lanzamiento.|
|**General** > **optimizar código**|A menos que un error sólo aparece en código optimizado, deje esta opción no está seleccionado para las compilaciones de depuración. Código optimizado es más difícil de depurar, porque las instrucciones no se corresponden directamente con las instrucciones en el código fuente.|
|**Salida** > **ruta de acceso de salida**|Normalmente se establece en *bin\Debug* para la depuración.|
|**Advanced** botón|Para obtener información sobre las opciones de depuración avanzadas, vea [cuadro de diálogo de configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). El formato portable para el símbolo (*.pdb*) archivos es un formato de multiplataforma recientes para aplicaciones de .NET Core.

## <a name="see-also"></a>Vea también
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)