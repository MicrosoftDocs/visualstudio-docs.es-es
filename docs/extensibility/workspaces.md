---
title: Áreas de trabajo en Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio usa un área de trabajo para representar una colección de archivos en la carpeta abierta, incluidos los proveedores y servicios del área de trabajo.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1ed660a5f52aba548d087b28f7caea4d1966fe45
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876953"
---
# <a name="workspaces"></a>Áreas de trabajo

Un área de trabajo es el modo en que Visual Studio representa cualquier colección de archivos en la [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)y se representa mediante el <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Por sí solo, el área de trabajo no entiende el contenido ni las características relacionadas con los archivos de la carpeta. En su lugar, proporciona un conjunto general de API para las características y las extensiones para generar y consumir datos sobre los que otros pueden actuar. Los productores se componen a través del [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) mediante varios atributos de exportación.

## <a name="workspace-providers-and-services"></a>Proveedores y servicios de áreas de trabajo

Los proveedores de áreas de trabajo y los servicios proporcionan los datos y la funcionalidad para reaccionar al contenido de un área de trabajo. Pueden proporcionar información de archivo contextual, símbolos en archivos de código fuente o funcionalidad de compilación.

Ambos conceptos usan un [patrón de fábrica](https://en.wikipedia.org/wiki/Factory_method_pattern) y el área de trabajo los importa a través de MEF. Todos los atributos de exportación implementan `IProviderMetadataBase` o `IWorkspaceServiceFactoryMetadata` , pero hay tipos concretos que las extensiones deben usar para los tipos exportados.

Una diferencia entre proveedores y servicios es su relación con el área de trabajo. Un área de trabajo puede tener muchos proveedores de un tipo determinado, pero solo se crea un servicio de un tipo determinado por área de trabajo. Por ejemplo, un área de trabajo tiene muchos proveedores de escáneres de archivos, pero el área de trabajo solo tiene un servicio de indexación por área de trabajo.

Otra diferencia clave es el consumo de datos de proveedores y servicios. El área de trabajo es el punto de entrada para obtener datos de los proveedores por un par de razones. En primer lugar, los proveedores suelen tener un conjunto estrecho de datos que crean. Los datos pueden ser símbolos para un archivo de código fuente de C# o contextos de archivo de compilación para un archivo de _CMakeLists.txt_ . El área de trabajo coincidirá con la solicitud de un consumidor a los proveedores cuyos metadatos se alineen con la solicitud. En segundo lugar, algunos escenarios permiten a muchos proveedores contribuir a una solicitud, mientras que otros escenarios usan el proveedor con la prioridad más alta.

En cambio, las extensiones pueden obtener instancias de e interactuar directamente con los servicios del área de trabajo. Los métodos de extensión de `IWorkspace` están disponibles para los servicios que proporciona Visual Studio, como <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . La extensión puede ofrecer un servicio de área de trabajo para los componentes de la extensión o para que los consuman otras extensiones. Los consumidores deben usar <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> o un método de extensión que proporcione en el `IWorkspace` tipo.

>[!WARNING]
> No cree servicios que entren en conflicto con Visual Studio. Puede provocar problemas inesperados.

## <a name="disposal-on-workspace-closure"></a>Eliminación en el cierre del área de trabajo

Al cerrar un área de trabajo, es posible que los extensores tengan que desechar pero llamar a código asincrónico. La <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interfaz está disponible para facilitar la escritura de este código.

## <a name="related-types"></a>Tipos relacionados

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> es la entidad central de un área de trabajo abierta como una carpeta abierta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> crea un proveedor por cada área de trabajo de la instancia.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> crea un servicio por cada área de trabajo de la instancia.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> debe implementarse en proveedores y servicios que necesiten ejecutar código asincrónico durante la eliminación.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> proporciona métodos auxiliares para tener acceso a servicios conocidos o a servicios arbitrarios.

## <a name="workspace-settings"></a>Configuración del área de trabajo

Las áreas de trabajo tienen un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servicio con un control sencillo pero eficaz sobre un área de trabajo. Para obtener información general básica de la configuración, consulte [Personalización de las tareas de compilación y depuración](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

La configuración de la mayoría de `SettingsType` los tipos son archivos _. JSON_ , como _VSWorkspaceSettings.jsen_ y _tasks.vs.jsen_.

La eficacia de la configuración del área de trabajo se centra en "ámbitos", que simplemente son rutas de acceso dentro del área de trabajo. Cuando un consumidor llama a <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , se agregan todos los ámbitos que incluyen la ruta de acceso y el tipo de configuración solicitados. La prioridad de agregación de ámbito es la siguiente:

1. "Configuración local", que suele ser el directorio raíz del área de trabajo `.vs` .
1. La ruta de acceso solicitada.
1. Directorio principal de la ruta de acceso solicitada.
1. Todos los directorios principales adicionales hasta la raíz del área de trabajo, inclusive.
1. "Configuración global", que se encuentra en un directorio de usuario.

El resultado es una instancia de <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Este objeto contiene la configuración de un tipo determinado y se puede consultar para establecer los nombres de clave almacenados como `string` . Los <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> métodos y los <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> métodos de extensión esperan que el llamador conozca el tipo del valor de configuración que se solicita. Como la mayoría de los archivos de configuración se guardan como archivos _. JSON_ , muchas invocaciones usarán `string` las matrices,, `bool` `int` y de esos tipos. También se admiten los tipos de objeto. En esos casos, puede usarse a `IWorkspaceSettings` sí mismo como argumento de tipo. Por ejemplo:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Suponiendo que esta configuración se encontraba en el _VSWorkspaceSettings.js_ de un usuario, se puede tener acceso a los datos de la siguiente manera:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Estas API de configuración no están relacionadas con las API disponibles en el `Microsoft.VisualStudio.Settings` espacio de nombres. La configuración del área de trabajo es independiente del host y usa archivos de configuración específicos del área de trabajo o proveedores de configuración dinámica.

### <a name="providing-dynamic-settings"></a>Proporcionar configuración dinámica

Las extensiones pueden proporcionar <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . Estos proveedores en memoria permiten a las extensiones agregar valores o invalidar otros.

Exportar un `IWorkspaceSettingsProvider` es diferente de otros proveedores de áreas de trabajo. El generador no es `IWorkspaceProviderFactory` y no hay ningún tipo de atributo especial. En su lugar, implemente <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> y use `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Al implementar métodos que devuelven `IWorkspaceSettingsSource` (como `IWorkspaceSettingsProvider.GetSingleSettings` ), devuelven una instancia de `IWorkspaceSettings` en lugar de `IWorkspaceSettingsSource` . `IWorkspaceSettings` proporciona más información que puede ser útil durante algunas agregaciones de configuración.

### <a name="settings-related-apis"></a>API relacionadas con la configuración

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> Lee y agrega la configuración del área de trabajo.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtiene el `IWorkspaceSettingsManager` para un área de trabajo.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtiene la configuración de un ámbito dado agregado en todos los ámbitos superpuestos.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene la configuración de un ámbito determinado.

## <a name="workspace-suggested-practices"></a>Prácticas sugeridas del área de trabajo

- Devuelva objetos de `IWorkspaceProviderFactory.CreateProvider` o API similares que recuerden su `Workspace` contexto cuando se crean. Se escriben interfaces de proveedores que esperan que este objeto se mantenga en creación.
- Guarde la configuración o las memorias caché específicas del área de trabajo en la ruta de acceso de "configuración local" del área de trabajo. Cree una ruta de acceso para el archivo con `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` en Visual Studio 2017, versión 15,6 o posterior. En el caso de las versiones anteriores a la 15,6, use el siguiente fragmento de código:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Eventos de solución y carga automática de paquetes

Los paquetes cargados pueden implementar `IVsSolutionEvents7` e invocar `IVsSolution.AdviseSolutionEvents` . Incluye eventos al abrir y cerrar una carpeta en Visual Studio.

Un contexto de la interfaz de usuario se puede usar para cargar automáticamente el paquete. El valor es `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Solución de problemas

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>El paquete SourceExplorerPackage no se cargó correctamente

La extensibilidad del área de trabajo está basada mucho en MEF y los errores de composición harán que el paquete que hospeda la carpeta abierta no se cargue. Por ejemplo, si una extensión exporta un tipo con `ExportFileContextProviderAttribute` , pero el tipo solo implementa `IWorkspaceProviderFactory<IFileContextActionProvider>` , se producirá un error al intentar abrir una carpeta en Visual Studio.

::: moniker range="vs-2017"

Los detalles del error se pueden encontrar en _%localappdata%\microsoft\visualstudio\ 15.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Resuelva los errores de los tipos implementados por la extensión.

::: moniker-end

::: moniker range=">=vs-2019"

Los detalles del error se pueden encontrar en _%localappdata%\microsoft\visualstudio\ 16.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Resuelva los errores de los tipos implementados por la extensión.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

* [Contextos de archivo](workspace-file-contexts.md) : los proveedores de contexto de archivo aportan inteligencia de código para las áreas de trabajo de carpeta abiertas.
* [Indexación](workspace-indexing.md) : la indexación de áreas de trabajo recopila y conserva información sobre el área de trabajo.
