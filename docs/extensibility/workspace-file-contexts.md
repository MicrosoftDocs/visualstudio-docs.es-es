---
title: Contextos de archivos del área de trabajo en Visual Studio | Microsoft Docs
description: Obtenga información sobre los proveedores de contexto de archivos que implementan la interfaz IFileContextProvider para admitir información en áreas de trabajo de carpeta abiertas.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 271b05d78123136d47cb618e8ed38cea64b7beac
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877070"
---
# <a name="workspace-file-contexts"></a>Contextos de archivo del área de trabajo

Toda la información de las áreas de trabajo de [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) se produce mediante "proveedores de contexto de archivo" que implementan la <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaz. Estas extensiones pueden buscar patrones en carpetas o archivos, leer archivos y archivos make de MSBuild, detectar dependencias de paquetes, etc. para acumular la información que necesitan para definir un contexto de archivo. Un contexto de archivo por sí mismo no realiza ninguna acción, sino que proporciona datos en los que otra extensión puede actuar.

Cada <xref:Microsoft.VisualStudio.Workspace.FileContext> tiene un `Guid` asociado que identifica el tipo de datos que lleva. Un área de trabajo lo usa `Guid` más adelante para hacerla coincidir con las extensiones que usan los datos a través de la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propiedad. Un proveedor de contexto de archivo se exporta con metadatos que identifican en qué contexto `Guid` de archivo pueden generar datos.

Una vez definido, un contexto de archivo puede asociarse a cualquier número de archivos o carpetas en el área de trabajo. Un archivo o una carpeta determinados pueden estar asociados a cualquier número de contextos de archivo. Se trata de una relación de varios a varios.

Los escenarios más comunes para los contextos de archivo están relacionados con los servicios de compilación, depuración y lenguaje. Para obtener más información, vea los otros temas relacionados con estos escenarios.

## <a name="file-context-lifecycle"></a>Ciclo de vida de contexto de archivo

Los ciclos de vida de un `FileContext` no son deterministas. En cualquier momento, un componente puede solicitar de forma asincrónica algún conjunto de tipos de contexto. Se consultarán los proveedores que admitan algún subconjunto de los tipos de contexto de solicitud. La `IWorkspace` instancia actúa como intermediario entre el consumidor y los proveedores a través del <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> método. Los consumidores pueden solicitar un contexto y realizar alguna acción a corto plazo basada en el contexto, mientras que otros pueden solicitar un contexto y mantener una referencia de larga duración.

Es posible que se produzcan cambios en los archivos que hacen que un contexto de archivo quede obsoleto. El proveedor puede desencadenar un evento en `FileContext` para notificar a los consumidores de las actualizaciones. Por ejemplo, si se proporciona un contexto de compilación para algún archivo pero un cambio en disco invalida ese contexto, el productor original puede invocar el evento. Cualquier consumidor que siga haciendo referencia `FileContext` a, podrá volver a consultar un nuevo `FileContext` .

>[!NOTE]
>No hay ningún modelo de inserciones para los consumidores. Los consumidores no recibirán notificaciones de los nuevos proveedores `FileContext` tras su solicitud.

## <a name="expensive-file-context-computations"></a>Cálculos de contexto de archivo caros

Leer el contenido del archivo desde el disco puede ser costoso, especialmente cuando un proveedor necesita resolver la relación entre archivos. Por ejemplo, se puede consultar un proveedor para el contexto de archivo de un archivo de código fuente, pero el contexto de archivo depende de los metadatos de un archivo de proyecto. Analizar el archivo de proyecto o evaluarlo con MSBuild es caro. En su lugar, la extensión puede exportar `IFileScanner` para crear `FileDataValue` datos durante la indización del área de trabajo. Ahora, cuando se le pidan contextos de archivo, el `IFileContextProvider` puede consultar rápidamente los datos indexados. Para obtener más información sobre la indexación, consulte el tema [indexación del área de trabajo](workspace-indexing.md) .

>[!WARNING]
>Tenga cuidado con otras formas en las que puede `FileContext` ser costoso calcular. Algunas interacciones de la interfaz de usuario son sincrónicas y dependen de un gran volumen de `FileContext` solicitudes. Algunos ejemplos son abrir una pestaña del editor y abrir un **Explorador de soluciones** menú contextual. Estas acciones realizan muchas solicitudes de tipo de contexto de compilación.

## <a name="file-context-related-apis"></a>API relacionadas con el contexto de archivo

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene datos y metadatos.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> y <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> crean el contexto del archivo.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exporta un proveedor de contexto de archivo.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> se usa para que los consumidores obtengan contextos de archivo.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> define los tipos de contexto de compilación que utilizará la carpeta abierta.

## <a name="file-context-actions"></a>Acciones de contexto de archivo

Aunque `FileContext` es solo datos sobre algunos archivos, una <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> es una manera de expresar y actuar en los datos. `IFileContextAction` es flexible en su uso. Dos de los casos más comunes son la compilación y la depuración.

## <a name="reporting-progress"></a>Notificación del progreso

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>Se pasa el método `IProgress<IFileContextActionProgressUpdate>` , pero el argumento no debe usarse como ese tipo. `IFileContextActionProgressUpdate` es una interfaz vacía y se puede invocar la llamada a `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` `NotImplementedException` . En su lugar, `IFileContextAction` debe convertir el argumento a otro tipo según sea necesario para el escenario.

Para obtener información sobre los tipos proporcionados por Visual Studio, consulte la documentación correspondiente del escenario.

## <a name="file-context-action-related-apis"></a>API relacionadas con la acción del contexto de archivo

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> ejecuta algún comportamiento basado en un `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crea instancias de `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exporta el tipo `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Inspección de archivos

Un área de trabajo escucha las notificaciones de cambio de archivo y proporciona el <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> a través de <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Los archivos que coincidan con la configuración "ExcludedItems" no generarán eventos de notificación de archivo. Un umbral entre eventos se usa para la simplificación de las notificaciones y la reducción de duplicados. Cuando necesite reaccionar a un cambio en un archivo, debe suscribirse a este servicio.

>[!TIP]
>El servicio de [indización](workspace-indexing.md) de un área de trabajo se suscribe a los eventos de archivo de forma predeterminada. Las adiciones y modificaciones de archivos harán que `IFileScanner` se invoquen eventos correspondientes para los nuevos datos de ese archivo. Las eliminaciones de archivos quitarán los datos indexados. No es necesario suscribirse `IFileScanner` al servicio File Watcher.

## <a name="next-steps"></a>Pasos siguientes

* [Indexación](workspace-indexing.md) : la indexación de áreas de trabajo recopila y conserva información sobre el área de trabajo.
* [Áreas de trabajo](workspaces.md) : revisar conceptos y configuración almacenamiento de áreas de trabajo.
