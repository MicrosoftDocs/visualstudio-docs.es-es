---
title: Área de trabajo de compilación en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143932"
---
# <a name="workspace-build"></a>Compilación de área de trabajo

Compatibilidad de compilación [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) escenarios requiere un dispositivo extender para proporcionar [indizadas](workspace-indexing.md) y [de contexto del archivo](workspace-file-contexts.md) datos para la [área de trabajo](workspaces.md), como así como la acción de compilación se ejecute.

A continuación se muestra un resumen de lo que tendrá la extensión.

## <a name="build-file-context"></a>Crear el contexto de archivo

- Generador del proveedor
  - `ExportFileContextProviderAttribute` atributo con `supportedContextTypeGuids` que todas las aplicables `string` constantes de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Proveedor de contexto de archivo
    - Devolver un `FileContext` para cada compilación operación y admitidos la configuración
      - `contextType` De <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con el `Configuration` propiedad como la configuración de compilación (por ejemplo `"Debug|x86"`, `"ret"`, o `null` si no es aplicable). O bien, utilizar una instancia de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. El valor de configuración **debe** coincide con la configuración del valor de datos de archivos indizados.

## <a name="indexed-build-file-data-value"></a>Valor de datos de archivo de compilación indizada

- Generador del proveedor
  - `ExportFileScannerAttribute` atributo con `IReadOnlyCollection<FileDataValue>` como un tipo compatible
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Analizador de archivos en `ScanContentAsync<T>`
  - Devuelve los datos cuando `FileScannerTypeConstants.FileDataValuesType` es el argumento de tipo
  - Devuelve un valor de datos de archivo para cada configuración que se construyó con:
    - `type` al igual que `BuildConfigurationContext.ContextTypeGuid`
    - `context` como la configuración de compilación (por ejemplo `"Debug|x86"`, `"ret"`, o `null` si no es aplicable). Este valor **debe** coincide con la configuración desde el contexto de archivo.

## <a name="build-file-context-action"></a>Acción de contexto del archivo de compilación

- Generador del proveedor
  - `ExportFileContextActionProvider` atributo con `supportedContextTypeGuids` que todas las aplicables `string` constantes de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Proveedor de la acción en `IFileContextActionProvider.GetActionsAsync`
  - Devolver un `IFileContextAction` que coincida con la determinada `FileContext.ContextType` valor
- Acción de contexto de archivos
  - Implementa `IFileContextAction` y <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` propiedad devuelve `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` es `0x1000` de compilación, `0x1010` para volver a generar, o `0x1020` para limpiar

>[!NOTE]
>Puesto que la `FileDataValue` necesario indexar, habrá cierta cantidad de tiempo entre abrir el área de trabajo y el punto en el que se analiza el archivo para la funcionalidad de generación completa. El retraso se verán en la primera apertura de una carpeta porque no hay ningún índice previamente almacenado en caché.

## <a name="reporting-messages-from-a-build"></a>Informar de los mensajes desde una compilación

La compilación puede aparecer mensajes de error, de advertencia y de información a los usuarios de dos maneras. La forma más sencilla es utilizar el <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> y proporcionar un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, de este modo:

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

`BuildMessage.Type` y `BuildMessage.LogMessage` controlan el comportamiento de donde se presenta información al usuario. Cualquier `BuildMessage.TaskType` valor distinto de `None` generará una **lista de errores** entrada con los detalles determinados. `LogMessage` siempre se generarán en el **generar** panel de la **salida** ventana de herramientas.

Como alternativa, las extensiones pueden interactuar directamente con el **lista de errores** o **generar** panel. Hay un error en las versiones anteriores a Visual Studio de 2017 versión 15,7 donde la `pszProjectUniqueName` argumento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> se omite.

>[!WARNING]
>Los llamadores de `IFileContextAction.ExecuteAsync` pueden proporcionar implementaciones subyacentes arbitrarias para el `IProgress<IFileContextActionProgressUpdate>` argumento. No invocar nunca `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` directamente. Actualmente no existen directrices generales para el uso de este argumento, pero estas instrucciones están sujetas a cambios.

## <a name="build-related-apis"></a>API relacionadas con la compilación

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Proporciona detalles de la configuración de compilación.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> muestra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s a los usuarios.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON y launch.vs.json

Para obtener información sobre cómo crear un archivo tasks.vs.json o launch.vs.json, consulte [personalizar la compilación y las tareas de depuración](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Pasos siguientes

* [Protocolo del servidor idioma](language-server-protocol.md) -Obtenga información acerca de cómo integrar los servidores de lenguaje en Visual Studio.