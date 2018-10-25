---
title: Las áreas de trabajo en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865835"
---
# <a name="workspaces"></a>Áreas de trabajo

Un área de trabajo es la forma en que Visual Studio representa una colección de archivos en [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), y se representa mediante el <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Por sí mismo, el área de trabajo no entiende el contenido o las características relacionadas con los archivos dentro de la carpeta. En su lugar, proporciona un conjunto de API para las características y extensiones para producir y consumir datos que otras personas pueden actuar en general. Los productores se crean a través de la [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) utilizando varios atributos de exportación.

## <a name="workspace-providers-and-services"></a>Servicios y proveedores de área de trabajo

Servicios y proveedores de área de trabajo proporcionan los datos y funciones para reaccionar ante el contenido de un área de trabajo. Es posible que proporcionan información contextual del archivo, símbolos de archivos de origen, o crear una funcionalidad.

Use ambos conceptos un [patrón factory](https://en.wikipedia.org/wiki/Factory_method_pattern) y se importa a través de MEF, el área de trabajo. Implementan todos los atributos de exportación `IProviderMetadataBase` o `IWorkspaceServiceFactoryMetadata`, pero hay tipos concretos que deben usar las extensiones para los tipos exportados.

Una diferencia entre los proveedores y servicios es su relación con el área de trabajo. Un área de trabajo puede tener muchos proveedores de un tipo determinado, pero solo un servicio de un tipo determinado se crea por área de trabajo. Por ejemplo, un área de trabajo tiene muchos proveedores de escáner de archivos, pero el área de trabajo tiene solo un servicio de indización por área de trabajo.

Otra diferencia clave es el consumo de datos de proveedores y servicios. El área de trabajo es el punto de entrada para obtener los datos de los proveedores por dos motivos. En primer lugar, los proveedores normalmente tienen un reducido conjunto de datos crean. Los datos podrían ser los símbolos para un C# del origen de archivo o crear contextos de archivo para un _CMakeLists.txt_ archivo. El área de trabajo hará coincidir la solicitud del consumidor a los proveedores cuyos metadatos se alinean con la solicitud. En segundo lugar, se permiten algunos escenarios para muchos proveedores para contribuir a una solicitud, mientras que otros escenarios de uso del proveedor con prioridad más alta.

En cambio, las extensiones de pueden obtener instancias de e interactuar directamente con los servicios de área de trabajo. Métodos de extensión en `IWorkspace` están disponibles para los servicios proporcionados por Visual Studio, como <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. La extensión puede ofrecer un servicio del área de trabajo de componentes dentro de la extensión o de otras extensiones que pueden consumir. Los consumidores deberían usar <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> o un método de extensión se proporciona en el `IWorkspace` tipo.

>[!WARNING]
> No crear servicios que entran en conflicto con Visual Studio. Puede provocar problemas inesperados.

## <a name="disposal-on-workspace-closure"></a>Eliminación de cierre del área de trabajo

En el cierre de un área de trabajo, podrían necesitar extensores dispose pero asincrónica se llama a código. El <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interfaz está disponible para facilitar la escritura de este código sencillo.

## <a name="related-types"></a>Tipos relacionados

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> es la entidad central para un área de trabajo abierto, como una carpeta abierta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> crea un proveedor por área de trabajo crea una instancia.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> crea un servicio por área de trabajo crea una instancia.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> se debe implementar en los proveedores y servicios que necesita para ejecutar código asincrónico durante la eliminación.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Proporciona métodos auxiliares para tener acceso a servicios conocidos o servicios arbitrarios.

## <a name="workspace-settings"></a>Configuración de área de trabajo

Áreas de trabajo tienen un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servicio simple pero eficaz control sobre un área de trabajo. Para obtener una introducción básica de configuración, consulte [personalización de compilación y depuración tareas](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Configuración para la mayoría `SettingsType` tipos son _.json_ archivos, tales como _VSWorkspaceSettings.json_ y _tasks.vs.json_.

La eficacia de la configuración de área de trabajo se centra en "ámbitos", que son simplemente las rutas de acceso del área de trabajo. Cuando un consumidor llama a <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, se agregan todos los ámbitos que incluyen la ruta de acceso solicitada y el tipo de configuración. Prioridad de la agregación de ámbito es como sigue:

1. "Configuración local", que normalmente es la raíz del área de trabajo `.vs` directory.
1. La ruta de acceso solicitada propio.
1. El directorio principal de la ruta de acceso solicitado.
1. Todos los primarios más directorios hasta e incluida la raíz del área de trabajo.
1. "Global settings", que se encuentra en un directorio de usuario.

El resultado es una instancia de <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Este objeto contiene la configuración de un tipo determinado y se puede consultar para establecer los nombres de clave almacenado como `string`. El <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> métodos y <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> métodos de extensión espera que el llamador saber el tipo del valor de configuración que se solicita. Como la mayoría de los archivos de configuración se almacenan como _.json_ archivos, usará muchas invocaciones `string`, `bool`, `int`y las matrices de esos tipos. También se admiten los tipos de objeto. En esos casos, puede usar `IWorkspaceSettings` como el argumento de tipo. Por ejemplo:

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

Suponiendo que esta configuración se encontraban en un usuario _VSWorkspaceSettings.json_, pueden tener acceso a los datos como:

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
>Esta configuración de las API no está relacionadas con las API disponibles en el `Microsoft.VisualStudio.Settings` espacio de nombres. Configuración de área de trabajo es independientes del host y usa archivos de configuración específica del área de trabajo o los proveedores de configuración dinámica.

### <a name="providing-dynamic-settings"></a>Proporcionar configuración dinámica

Pueden proporcionar extensiones <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Estos proveedores en memoria permiten las extensiones agregar la configuración o reemplazar otras.

Exportar un `IWorkspaceSettingsProvider` es diferente de otros proveedores de área de trabajo. El generador no es `IWorkspaceProviderFactory` y no hay ningún tipo de atributo especial. En su lugar, implemente <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> y usar `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

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
>Al implementar los métodos que devuelven `IWorkspaceSettingsSource` (como `IWorkspaceSettingsProvider.GetSingleSettings`), devolver una instancia de `IWorkspaceSettings` lugar `IWorkspaceSettingsSource`. `IWorkspaceSettings` proporciona más información que puede ser útil durante algunos agregaciones de configuración.

### <a name="settings-related-apis"></a>API relacionadas con la configuración

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> lee y agrega la configuración de área de trabajo.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtiene el `IWorkspaceSettingsManager` para un área de trabajo.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtiene la configuración de un determinado ámbito agregado a través de todos los ámbitos que se superponen.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene la configuración para un ámbito determinado.

## <a name="workspace-suggested-practices"></a>Área de trabajo sugerido recomendados

- Devolver los objetos de `IWorkspaceProviderFactory.CreateProvider` o API similares que recordar sus `Workspace` contexto cuando se creó. Interfaces de los proveedores se escriben espera que este objeto se mantiene en la creación.
- Guardar cachés específicas del área de trabajo o los valores de la ruta de acceso de "Configuración Local" del área de trabajo. Crear una ruta de acceso para el archivo mediante `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` en Visual Studio 2017 versión 15.6 o posterior. Las versiones anteriores a la versión 15.6, use el siguiente fragmento de código:

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

## <a name="solution-events-and-package-auto-load"></a>Eventos de la solución y cargar paquete automáticamente

Pueden implementar paquetes cargados `IVsSolutionEvents7` e invocar `IVsSolution.AdviseSolutionEvents`. Incluye eventos de apertura y cierre de una carpeta en Visual Studio.

Un contexto de interfaz de usuario puede utilizarse para cargar automáticamente el paquete. El valor es `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Solución de problemas

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>No se cargó correctamente el paquete SourceExplorerPackage

Extensibilidad de área de trabajo es principalmente basado en MEF y errores de composición hará que el paquete que hospeda la carpeta abierta para que no se pudo cargar. Por ejemplo, si una extensión exporta un tipo con `ExportFileContextProviderAttribute`, pero sólo implementa el tipo `IWorkspaceProviderFactory<IFileContextActionProvider>`, se producirá un error al intentar abrir una carpeta en Visual Studio. Detalles del error pueden encontrarse en _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Resuelva los errores para los tipos implementados por la extensión.

## <a name="next-steps"></a>Pasos siguientes

* [Contextos de archivo](workspace-file-contexts.md) -capturadores de contexto de archivo proporcionan inteligencia de código para las áreas de trabajo de la carpeta abierta. 
* [Indexación](workspace-indexing.md) -área de trabajo de indexación recopila y se conserva la información sobre el área de trabajo.
