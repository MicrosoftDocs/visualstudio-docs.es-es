---
title: API eliminadas en Visual Studio versión preliminar de 2022
description: Obtenga información sobre las API de VS SDK eliminadas en Visual Studio 2022 Preview, para que los autores de extensiones actualicen sus extensiones para que funcionen con Visual Studio versión preliminar de 2022.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308616"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio API quitadas del SDK de 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Las API siguientes se han quitado del SDK de Visual Studio y ya no se pueden usar; consulte cada sección para obtener más información sobre cómo actualizar el código.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` Y `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Carga de solución asincrónica y carga de solución ligera](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Abrir desde código fuente seguro](#open-from-source-safe)
* [Nuevos Diseñador XAML WPF para .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

se `IVsImageService` quita en Visual Studio 2022. En su `IVsImageService` lugar, todos los usuarios de deben `IVsImageService2` pasar a .

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Si usa `IVsImageService` , reemplace las llamadas a sus métodos por llamadas a métodos equivalentes en `IVsImageService2` :

| **IVsImageService (método)** | **Método IVsImageService2 equivalente** |
|----------------------------|----------------------------------------|
| Sumar                        | AddCustomImage                         |
| Obtener                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`Los métodos Add y Get de se refieren a imágenes personalizadas por nombre (una cadena), en lugar de a un moniker.  Es preferible cambiar el código para usar solo monikers para hacer referencia a imágenes personalizadas, pero si esto resulta poco práctico tiene un par de métodos que le permitirán asociar un nombre a un `IVsImageService2` moniker:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Con esos dos métodos, puede seguir haciendo referencia a imágenes por nombre.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

Los `IBlockContextProvider` tipos y relacionados se quitan en Visual Studio 2022. En su `IBlockContextProvider` lugar, todos los usuarios de deben `IStructureContextSourceProvider` pasar a .

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Los usuarios `IBlockContextProvider` de deben usar en su lugar ( `IStructureContextSourceProvider` [documentación](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>IToolTipProvider

Los `IToolTipProvider` tipos y relacionados se quitan en Visual Studio 2022. En su `IToolTipProvider` lugar, todos los usuarios de deben `IToolTipService` pasar a .

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Los usuarios `IToolTipProvider` de deben usar en su lugar ( `IToolTipService` [documentación](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner e IVsFullTextScanner

y `IVsTextScanner` `IVsFullTextScanner` se quitan en Visual Studio 2022. En su lugar, `IVsTextScanner` todos los usuarios de o deben pasar a `IVsFullTextScanner` `IVsTextLines` .

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Los usuarios `IVsTextScanner` de o deben usar en su lugar ( `IVsFullTextScanner` `IVsTextLines` [documentación](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Carga de solución asincrónica y carga de solución ligera

Las características carga de solución asincrónica (ASL) y carga de solución ligera (LSL) se quitan en Visual Studio 2022, por lo que se quitan los métodos siguientes:

### <a name="interfaces"></a>Interfaces

* `IVsSolution4` - Métodos: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` - Métodos: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` - Interfaz completa
* `IVsSolutionLoadManager` - Interfaz completa
* `IVsSccManager3`  - Interfaz completa
* `IVsAsynchronousProjectCreate` - Interfaz completa
* `IVsAsynchronousProjectCreateUI` - Interfaz completa

### <a name="enums-properties-and-ui-contexts"></a>Enumeraciones, propiedades y contextos de interfaz de usuario

* `VSHPROPID_ProjectUnloadStatus` - Enumeración: `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Ninguno.

## <a name="ivsdummy"></a>IVsDummy

se `IVsDummy` quita en Visual Studio 2022 y no se reemplazará. 

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Ninguno. Sin embargo, no debería tener ningún impacto, ya que la API no hizo nada.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft.VisualStudio.Shell.Task

Se ha cambiado el nombre de la `Microsoft.VisualStudio.Shell.Task` clase a para que no entre en conflicto con la clase muy `Microsoft.VisualStudio.Shell.TaskListItem` `System.Threading.Tasks.Task` popular.

## <a name="open-from-source-safe"></a>Abrir desde código fuente seguro

Se está quitando la compatibilidad para abrir una solución desde el origen seguro, por lo que se están quitando los siguientes métodos, eventos y constantes.

## <a name="interfaces"></a>Interfaces

* `IVsSCCProvider3` - Interfaz completa

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Ninguno.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Nuevos Diseñador XAML WPF para .NET Framework

El Diseñador XAML de WPF actual para .NET Framework ha quedado en desuso y se reemplazará por un nuevo Diseñador XAML de WPF para .NET Framework, en función de la misma arquitectura usada para wpf Diseñador XAML para .NET (.NET Core). Esto también significa que wpf .NET Framework modelo de extensibilidad de control basado en .design.dll y Microsoft.Windows.Design.Extensibility ya no se admite. El nuevo Diseñador XAML WPF para .NET Framework proporcionará el mismo modelo de extensibilidad que wpf Diseñador XAML para .NET (.NET Core). Si ya ha creado una extensión .designtools.dll para .NET (.NET Core), esa misma extensión funcionará para el nuevo Diseñador XAML WPF para .NET Framework. Consulte el vínculo de migración siguiente para obtener más información sobre cómo migrar al nuevo modelo de extensibilidad para plataformas WPF (.NET Framework y .NET Core) y plataformas para UWP en el futuro. 

### <a name="recommended-updates"></a>Actualizaciones recomendadas

Vea [Migración de extensibilidad del diseñador XAML.](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)
