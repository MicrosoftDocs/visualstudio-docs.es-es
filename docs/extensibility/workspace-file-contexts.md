---
title: Contextos de archivo del área de trabajo en Visual Studio | Documentos de Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952820"
---
# <a name="workspace-file-contexts"></a>Contextos de archivo del área de trabajo

Toda la información en [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) las áreas de trabajo producidos por "archivo capturadores de contexto" que implementan el <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaz. Estas extensiones pueden buscar patrones en carpetas o archivos, leer los archivos de MSBuild y archivos MAKE, detectan las dependencias del paquete, etc. con el fin de acumular los conocimientos que necesitan para definir un contexto de archivo. Un contexto de archivo por sí solo no realiza ninguna acción, pero en su lugar, proporciona datos que otra extensión, a continuación, puede actuar en.

Cada <xref:Microsoft.VisualStudio.Workspace.FileContext> tiene un `Guid` asociado que identifica el tipo de datos se lleva. Un área de trabajo usa esto `Guid` más adelante para que coincidan con las extensiones que consumen los datos a través de la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propiedad. Un proveedor de contexto de archivo se exporta con metadatos que identifica qué contexto de archivo `Guid`s puede generar datos de.

Una vez definido, un contexto de archivo puede asociarse con cualquier número de archivos o carpetas en el área de trabajo. Un determinado archivo o carpeta puede asociarse con cualquier número de contextos de archivo. Es una relación varios a varios.

Los escenarios más comunes para los contextos de archivo están relacionados con la compilación, depuración y servicios de lenguaje. Para obtener más información, consulte los otros temas relacionados con estos escenarios.

## <a name="file-context-lifecycle"></a>Ciclo de vida del contexto de archivo

Los ciclos de vida para un `FileContext` son no deterministas. En cualquier momento, un componente de forma asincrónica puede solicitar para algún conjunto de tipos de contexto. Los proveedores que admiten un subconjunto de los tipos de contexto de solicitud que se va a consultar. El `IWorkspace` instancia actúa como intermediario entre los consumidores y proveedores a través de la <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> método. Los consumidores pueden solicitar un contexto y realizar alguna acción a corto plazo en función del contexto, mientras que otros usuarios pueden solicitar un contexto y mantener una referencia de larga duración.

Es posible que realizan los cambios en los archivos que provocan un contexto de archivo a quedar obsoleto. El proveedor puede desencadenar un evento en el `FileContext` para notificar a los consumidores de las actualizaciones. Por ejemplo, si se proporciona un contexto de compilación para algunos archivos, pero ese contexto invalida un cambio en el disco, el productor original puede invocar el evento. Los consumidores que siguen haciendo referencia a ella `FileContext` , a continuación, puede volver a consultar un nuevo `FileContext`.

>[!NOTE]
>No hay ningún modelo de inserción a los consumidores. Los consumidores no recibirá notificación de un proveedor nuevo `FileContext` después de su solicitud.

## <a name="expensive-file-context-computations"></a>Cálculos del contexto de archivos costosas

Contenido del archivo de lectura de disco puede ser costoso, especialmente cuando se necesita resolver la relación entre los archivos de un proveedor. Por ejemplo, puede consultar un proveedor de contexto del archivo de algún archivo de código fuente, pero el contexto del archivo es dependiente de los metadatos de un archivo de proyecto. Analizar el archivo de proyecto o evaluarlo con MSBuild es costosa. En su lugar, puede exportar la extensión de un `IFileScanner` crear `FileDataValue` datos durante la indización de área de trabajo. Ahora cuando se le pida para contextos de archivo, el `IFileContextProvider` puede consultar rápidamente para los datos indizados. Para obtener más información sobre la indexación, consulte el [área de trabajo de indexación](workspace-indexing.md) tema.

>[!WARNING]
>Tenga cuidado de otras formas de su `FileContext` podría ser costoso calcular. Algunos tipos de interacción de la interfaz de usuario son sincrónicos y se basan en un gran volumen de `FileContext` solicitudes. Algunos ejemplos son abrir una pestaña del editor y abrir un **el Explorador de soluciones** menú contextual. Estas acciones hacer que el contexto de compilación muchas solicitudes de tipo.

## <a name="file-context-related-apis"></a>API relacionadas con el contexto de archivo

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene los datos y metadatos.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> y <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> crear el contexto del archivo.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exporta un proveedor de contexto de archivo.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> se usa para los consumidores para obtener los contextos de archivo.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> define los tipos de contexto de compilación que consumirá la carpeta abierta.

## <a name="file-context-actions"></a>Acciones de contexto de archivo

Mientras un `FileContext` sí es simplemente datos acerca de algunos archivos, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> es una manera de express y actuar sobre esos datos. `IFileContextAction` es flexible en su uso. Dos de los casos más comunes son compilar y depurar.

## <a name="reporting-progress"></a>Informes de progreso

El <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> se pasa al método `IProgress<IFileContextActionProgressUpdate>`, pero el argumento no debe usarse como ese tipo. `IFileContextActionProgressUpdate` es una interfaz vacía e invocar `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` podría producir `NotImplementedException`. En su lugar, el `IFileContextAction` debe convertir el argumento a otro tipo según sea necesario para el escenario.

Para obtener información sobre los tipos proporcionados por Visual Studio, consulte la documentación del escenario respectivo.

## <a name="file-context-action-related-apis"></a>API relacionadas con la acción contextual de archivo

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> algunos comportamientos según se ejecuta un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crea instancias de `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exporta el tipo `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Inspección de archivos

Un área de trabajo escucha las notificaciones de cambio y proporciona el <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> a través de <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Archivos que coinciden con la configuración de "ExcludedItems" no producirá los eventos de notificación de archivos. Un umbral entre los eventos se usa para la reducción duplicado y simplificación de la notificación. Cuando necesite responder a un cambio de archivo, debe suscribirse a este servicio.

>[!TIP]
>Un área de trabajo [servicio de indización](workspace-indexing.md) se suscribe a eventos de archivo de forma predeterminada. Archivo adiciones y modificaciones provocará relevantes `IFileScanner`eventos s que se invocará para los nuevos datos para ese archivo. Las eliminaciones de archivos quitarán los datos indizados. No es necesario suscribirse su `IFileScanner` para el servicio de Monitor de archivos.

## <a name="next-steps"></a>Pasos siguientes

* [Indexación](workspace-indexing.md) -área de trabajo de indexación recopila y se conserva la información sobre el área de trabajo.
* [Las áreas de trabajo](workspaces.md) -revisar los conceptos de área de trabajo y de almacenamiento de configuración.
