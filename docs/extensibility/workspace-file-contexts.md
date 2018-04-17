---
title: Contextos de archivo de área de trabajo en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-file-contexts"></a>Contextos de archivo de área de trabajo

Todas las visiones [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) áreas de trabajo son generadas por "archivo proveedores de contexto" que implementan el <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaz. Estas extensiones pueden buscar patrones en carpetas o archivos, leer los archivos de MSBuild y archivos MAKE, detectan dependencias de paquetes, etc. para acumular la información que necesitan para definir un contexto de archivo. Un contexto de archivo por sí solo no realiza ninguna acción, pero en su lugar proporciona datos que otra extensión, a continuación, puede actuar en.

Cada <xref:Microsoft.VisualStudio.Workspace.FileContext> tiene un `Guid` asociado que identifica el tipo de datos se realiza. Un área de trabajo utiliza este `Guid` una versión posterior para que coincidan con las extensiones que consumen los datos a través de la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propiedad. Un proveedor de contexto de archivo se exporta con metadatos que identifican qué contexto archivo `Guid`s puede generar datos de.

Una vez definido, un contexto de archivo se puede asociar con cualquier número de archivos o carpetas en el área de trabajo. Un determinado archivo o carpeta puede asociarse a cualquier número de contextos de archivo. Es una relación de varios a varios.

Los escenarios más comunes para contextos de archivo están relacionados con la compilación, depuración y servicios de lenguaje. Para obtener más información, consulte los otros temas relacionados con estos escenarios.

## <a name="file-context-lifecycle"></a>Ciclo de vida del contexto de archivo

Los ciclos de vida de un `FileContext` son no deterministas. En cualquier momento, un componente de forma asincrónica puede solicitar para algún conjunto de tipos de contexto. Los proveedores que admiten un subconjunto de los tipos de contexto de solicitud que se van a consultar. El `IWorkspace` instancia actúa como el hombre intermedio entre los consumidores y proveedores a través de la <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> método. Los consumidores pueden solicitar un contexto y realizar alguna acción a corto plazo en función del contexto, mientras que otros podrían un contexto de la solicitud y mantener una referencia de larga duración. 

Pueden ocurrir cambios a los archivos que provocan un contexto de archivo a quedar obsoleto. El proveedor puede desencadenar un evento en el `FileContext` para notificar a los consumidores de las actualizaciones. Por ejemplo, si se proporciona un contexto de la creación de algunos archivos, pero ese contexto invalida un cambio en el disco, el productor original puede invocar el evento. Los consumidores sigue haciendo referencia a ella `FileContext` , a continuación, puede volver a consultar un nuevo `FileContext`.

>[!NOTE]
>No hay ningún modelo de inserción a los consumidores. No se le notificará a los consumidores de un proveedor nuevo `FileContext` después de su solicitud.

## <a name="expensive-file-context-computations"></a>Cálculos de contexto de archivos costosas

Contenido del archivo de lectura de disco puede ser costoso, especialmente cuando es necesario un proveedor resolver la relación entre archivos. Por ejemplo, es posible consultar un proveedor de contexto del archivo de algunos archivos de origen, pero el contexto de archivo depende de los metadatos de un archivo de proyecto. Analizar el archivo de proyecto o evaluar con MSBuild es costoso. En su lugar, puede exportar la extensión de un `IFileScanner` para crear `FileDataValue` datos durante la indización de área de trabajo. Ahora cuando se le pregunte para contextos de archivo, el `IFileContextProvider` rápidamente puede consultar los datos indizados. Para obtener más información sobre la indización, consulte la [indización de área de trabajo](workspace-indexing.md) tema.

>[!WARNING]
>Tenga cuidado de otras maneras de su `FileContext` podría ser costosa calcular. Algunos tipos de interacción de la interfaz de usuario son sincrónicas y se basan en un gran volumen de `FileContext` solicitudes. Algunos ejemplos son abrir una pestaña de editor y abrir un **el Explorador de soluciones** menú contextual. Estas acciones hacer que el contexto de compilación muchas solicitudes de tipo.

## <a name="file-context-related-apis"></a>API relacionadas con el contexto de archivo

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene los datos y metadatos.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> y <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> crear el contexto de archivo.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exporta un proveedor de contexto de archivo.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> se utiliza para los consumidores para obtener los contextos de archivo.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> define los tipos de contexto de compilación que consumirá la carpeta abierta.

## <a name="file-context-actions"></a>Acciones del contexto de archivos

Mientras un `FileContext` es solo los datos acerca de alguno de los archivos, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> es una manera de express y actuar en los datos. `IFileContextAction` es flexible en su uso. Dos de sus casos más comunes son compilar y depurar.

## <a name="reporting-progress"></a>Notificar el progreso

El <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> se pasa al método `IProgress<IFileContextActionProgressUpdate>`, pero el argumento no debe utilizarse como ese tipo. `IFileContextActionProgressUpdate` es una interfaz vacía e invocar `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` podría producir `NotImplementedException`. En su lugar, el `IFileContextAction` debe convertir el argumento en otro tipo según sea necesario para el escenario.

Para obtener información sobre los tipos proporcionados por Visual Studio, consulte la documentación del escenario respectivo.

## <a name="file-context-action-related-apis"></a>API relacionadas con la acción de contexto de archivos

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> ejecuta algún comportamiento tomando como base un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crea instancias de `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exporta el tipo de `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Inspección de archivos

Un área de trabajo escucha las notificaciones de cambio de archivo y proporciona el <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> a través de <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Archivos que coincidan con la configuración de "ExcludedItems" no producirá los eventos de notificación de archivo. Un umbral entre los eventos se usa para simplificación de notificación y reducción duplicada. Cuando necesite responder a un cambio de archivo, debe suscribirse a este servicio.

>[!TIP]
>Un área de trabajo [servicio de indización](workspace-indexing.md) se suscribe a eventos de archivo de forma predeterminada. Archivo adiciones y modificaciones provocará relevante `IFileScanner`eventos s que se debe invocar para los nuevos datos para ese archivo. Eliminaciones de archivos quitarán los datos indizados. No es necesario suscribirse su `IFileScanner` para el servicio de Monitor de archivos.

## <a name="next-steps"></a>Pasos siguientes

* [Indización](workspace-indexing.md) -indización de área de trabajo se recopila y se conserva la información sobre el área de trabajo.
* [Áreas de trabajo](workspaces.md) -Revisar conceptos de área de trabajo y el almacenamiento de configuración.
