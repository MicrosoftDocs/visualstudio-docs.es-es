---
title: Área de trabajo de compilación en Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: b0d90a3d317583e987eae83fadae5afa40546701
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826726"
---
# <a name="workspace-build"></a>Compilación de área de trabajo

Soporte técnico de compilación [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) escenarios requiere un objeto extender para proporcionar [indizada](workspace-indexing.md) y [contexto del archivo](workspace-file-contexts.md) datos para el [área de trabajo](workspaces.md), como así como la acción de compilación se ejecute.

A continuación es un resumen de lo que tendrá la extensión.

## <a name="build-file-context"></a>Contexto de archivo de compilación

- Generador del proveedor
  - `ExportFileContextProviderAttribute` atributo con `supportedContextTypeGuids` como todos los aplicables `string` constantes de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Proveedor de contexto de archivo
    - Devolver un `FileContext` para cada compilación operación y se admite la configuración
      - `contextType` De <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con el `Configuration` propiedad como la configuración de compilación (por ejemplo `"Debug|x86"`, `"ret"`, o `null` si no es aplicable). Como alternativa, use una instancia de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. El valor de configuración **debe** coinciden con la configuración del valor de datos de archivos indizados.

## <a name="indexed-build-file-data-value"></a>Valor de datos de archivo de compilación indizada

- Generador del proveedor
  - `ExportFileScannerAttribute` atributo con `IReadOnlyCollection<FileDataValue>` como un tipo compatible
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Analizador de archivos en `ScanContentAsync<T>`
  - Devuelve los datos cuando `FileScannerTypeConstants.FileDataValuesType` es el argumento de tipo
  - Devuelve un valor de datos de archivo para cada configuración que se construye con:
    - `type` como `BuildConfigurationContext.ContextTypeGuid`
    - `context` como la configuración de compilación (por ejemplo `"Debug|x86"`, `"ret"`, o `null` si no es aplicable). Este valor **debe** coinciden con la configuración desde el contexto del archivo.

## <a name="build-file-context-action"></a>Acción de contexto de archivo de compilación

- Generador del proveedor
  - `ExportFileContextActionProvider` atributo con `supportedContextTypeGuids` como todos los aplicables `string` constantes de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Proveedor de la acción en `IFileContextActionProvider.GetActionsAsync`
  - Devolver un `IFileContextAction` que coincida con la determinada `FileContext.ContextType` valor
- Acción contextual de archivo
  - Implementa `IFileContextAction` y <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` propiedad devuelve `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` es `0x1000` para compilación, `0x1010` para volver a generar, o `0x1020` para limpiar

>[!NOTE]
>Puesto que el `FileDataValue` necesario indexar, habrá cierta cantidad de tiempo entre abrir el área de trabajo y el punto en el que se analiza el archivo para la funcionalidad de compilación completa. El retraso se verá en el abrir primero de una carpeta porque no hay ningún índice previamente almacenado en caché.

## <a name="reporting-messages-from-a-build"></a>Informar de los mensajes de una compilación

La compilación puede exponer información, advertencia y mensajes de error a los usuarios de dos maneras. La forma más sencilla es usar el <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> y proporcionar un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, así:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` y `BuildMessage.LogMessage` controlan el comportamiento de donde se presenta información al usuario. Cualquier `BuildMessage.TaskType` otro valor distinto `None` generará un **lista de errores** entrada con los detalles proporcionados. `LogMessage` siempre se mostrarán en el **compilar** panel de la **salida** ventana de herramientas.

Como alternativa, las extensiones pueden interactuar directamente con el **lista de errores** o **compilar** panel. Hay un error en las versiones anteriores de Visual Studio 2017 versión 15.7 donde el `pszProjectUniqueName` argumento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> se omite.

>[!WARNING]
>Los autores de llamadas de `IFileContextAction.ExecuteAsync` puede proporcionar implementaciones subyacentes arbitrarias para la `IProgress<IFileContextActionProgressUpdate>` argumento. No invocar nunca `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` directamente. Actualmente no hay ningún directrices generales para usar este argumento, pero estas directrices están sujetos a cambios.

## <a name="build-related-apis"></a>API relacionadas con la compilación

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Proporciona los detalles de configuración de compilación.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> muestra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s a los usuarios.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON y launch.vs.json

Para obtener información sobre la creación de un archivo tasks.vs.json o launch.vs.json, consulte [personalización de compilación y depuración tareas](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Pasos siguientes

* [Protocolo del servidor idioma](language-server-protocol.md) -Obtenga información sobre cómo integrar servidores de lenguaje en Visual Studio.