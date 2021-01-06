---
title: Compilación del área de trabajo en Visual Studio | Microsoft Docs
description: Obtenga información sobre el extensor que proporciona datos indexados y de contexto de archivo de un área de trabajo para admitir un escenario de carpeta abierta.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: e44c2398b873bbca95c971ae1b44ac3de831b2ae
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877109"
---
# <a name="workspace-build"></a>Compilación del área de trabajo

La compatibilidad con la compilación en los escenarios de [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) requiere un objeto extender para proporcionar los datos [indizados](workspace-indexing.md) y de [contexto de archivo](workspace-file-contexts.md) para el [área de trabajo](workspaces.md), así como la acción de compilación que se va a ejecutar.

A continuación se muestra un esquema de lo que necesitará la extensión.

## <a name="build-file-context"></a>Contexto del archivo de compilación

- Generador de proveedores
  - `ExportFileContextProviderAttribute` atributo con `supportedContextTypeGuids` como todas las `string` constantes aplicables de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Proveedor de contexto de archivo
    - Devolver un `FileContext` para cada operación de compilación y configuración admitida
      - `contextType` de <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con la `Configuration` propiedad como la configuración de compilación (por ejemplo `"Debug|x86"` , `"ret"` o `null` si no es aplicable). También puede usar una instancia de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . El valor de configuración **debe** coincidir con la configuración del valor de datos de archivo indexado.

## <a name="indexed-build-file-data-value"></a>Valor de datos del archivo de compilación indizado

- Generador de proveedores
  - `ExportFileScannerAttribute` atributo con `IReadOnlyCollection<FileDataValue>` como tipo compatible
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Escáner de archivos activado `ScanContentAsync<T>`
  - Devuelve datos cuando `FileScannerTypeConstants.FileDataValuesType` es el argumento de tipo.
  - Devuelve un valor de datos de archivo para cada configuración construida con:
    - `type` aplicar `BuildConfigurationContext.ContextTypeGuid`
    - `context` como configuración de compilación (por ejemplo `"Debug|x86"` , `"ret"` o `null` si no es aplicable). Este valor **debe** coincidir con la configuración del contexto del archivo.

## <a name="build-file-context-action"></a>Acción de contexto del archivo de compilación

- Generador de proveedores
  - `ExportFileContextActionProvider` atributo con `supportedContextTypeGuids` como todas las `string` constantes aplicables de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Proveedor de acciones en `IFileContextActionProvider.GetActionsAsync`
  - Devuelve un `IFileContextAction` que coincide con el `FileContext.ContextType` valor especificado.
- Acción de contexto de archivo
  - Implementa `IFileContextAction` y <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` la propiedad devuelve `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` es `0x1000` para compilación, `0x1010` para recompilar o `0x1020` para limpiar

>[!NOTE]
>Dado que es `FileDataValue` necesario indizar, habrá un período de tiempo entre abrir el área de trabajo y el punto en el que se examina el archivo para detectar la funcionalidad de compilación completa. El retraso se verá en la primera apertura de una carpeta porque no hay ningún índice previamente almacenado en caché.

## <a name="reporting-messages-from-a-build"></a>Informes de mensajes de una compilación

La compilación puede mostrar mensajes de información, ADVERTENCIA y error a los usuarios de una de estas dos maneras. La manera más sencilla es usar <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> y proporcionar un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , como:

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

`BuildMessage.Type` y `BuildMessage.LogMessage` controlan el comportamiento de dónde se presenta la información al usuario. Cualquier `BuildMessage.TaskType` valor distinto de producirá `None` una entrada **lista de errores** con los detalles especificados. `LogMessage` siempre se generará en el panel **compilar** de la ventana de herramientas de **salida** .

Como alternativa, las extensiones pueden interactuar directamente con el panel de **lista de errores** o **compilación** . Existe un error en las versiones anteriores a Visual Studio 2017, versión 15,7, donde `pszProjectUniqueName` se omite el argumento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> .

>[!WARNING]
>Los llamadores de `IFileContextAction.ExecuteAsync` pueden proporcionar implementaciones subyacentes arbitrarias para el `IProgress<IFileContextActionProgressUpdate>` argumento. Nunca se invoca `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` directamente. Actualmente no hay instrucciones generales para usar este argumento, pero estas instrucciones están sujetas a cambios.

## <a name="build-related-apis"></a>Compilación de API relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> proporciona detalles de configuración de la compilación.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> muestra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> s a los usuarios.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jsy launch.vs.jsen

Para obtener información sobre cómo crear un tasks.vs.jsen o launch.vs.jsen el archivo, vea [personalizar las tareas de compilación y depuración](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Pasos siguientes

* [Protocolo del servidor de lenguaje](language-server-protocol.md) : Obtenga información sobre cómo integrar servidores de idioma en Visual Studio.