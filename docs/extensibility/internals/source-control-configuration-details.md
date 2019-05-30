---
title: Detalles de configuración de Control de origen | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 917354534ee3dbb2b615ec031f0a41c31bd88235
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322580"
---
# <a name="source-control-configuration-details"></a>Detalles de configuración del control de código fuente
Para poder implementar el control de código fuente, es preciso configurar correctamente el sistema de proyecto o el editor para hacer lo siguiente:

- Solicitar permiso para realizar la transición al estado cambiado

- Solicitar permiso para guardar un archivo

- Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos del proyecto

## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permiso para realizar la transición al estado cambiado
 Un editor o proyecto debe solicitar permiso para realizar la transición al estado cambiado (modificado) mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y recibir la aprobación para cambiar el documento desde el entorno antes de devolver `True` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Un proyecto es esencialmente un editor para un archivo de proyecto y, como resultado, tiene la misma responsabilidad para implementar el seguimiento de estado cambiado del archivo de proyecto como un editor de texto que se hace para sus archivos. El entorno controla el cambio de estado de la solución, pero debe controlar el cambio de estado de cualquier objeto que hace referencia a la solución, pero no almacene, como un archivo de proyecto o sus elementos. En general, si su editor o proyecto es responsable de administrar la persistencia para un elemento, es responsable de implementar el seguimiento de estado cambiado.

 En respuesta a la `IVsQueryEditQuerySave2::QueryEditFiles` llama, el entorno puede hacer lo siguiente:

- Rechazar la llamada a cambiar, en cuyo caso el editor o proyecto debe permanecer en estado unchanged (limpio).

- Indicar que se deben recargar los datos del documento. Para un proyecto, el entorno se volverá a cargar los datos para el proyecto. Un editor debe volver a cargar los datos desde el disco a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementación. En cualquier caso, puede cambiar el contexto en el proyecto o el editor cuando se vuelve a cargar los datos.

  Es una tarea compleja y difícil volver a plantear adecuado `IVsQueryEditQuerySave2::QueryEditFiles` llamadas a un código base existente. Como resultado, se deben integrar estas llamadas durante la creación del proyecto o del editor.

## <a name="request-permission-to-save-a-file"></a>Solicitar permiso para guardar un archivo
 Antes de que un proyecto o un editor guarde un archivo, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Los archivos de proyecto, estas llamadas se completan automáticamente mediante la solución, que se sabe cuándo se debe guardar un archivo de proyecto. Editores son responsables de realizar estas llamadas a menos que la implementación del editor de `IVsPersistDocData2` usa la función auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Si el editor implementa `IVsPersistDocData2` en este modo, a continuación, la llamada a `IVsQueryEditQuerySave2::QuerySaveFile` o `IVsQueryEditQuerySave2::QuerySaveFiles` se llevan a cabo.

> [!NOTE]
> Siempre realice estas llamadas de forma preventiva, es decir, en un momento en el editor puede recibir una cancelación.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos del proyecto
 Antes de que un proyecto puede agregar, cambiar o quitar un archivo o directorio, debe llamar a la correspondiente `IVsTrackProjectDocuments2::OnQuery*` método para solicitar permiso desde el entorno. Si se concede permiso, entonces el proyecto debe completar la operación y, a continuación, llame al `IVsTrackProjectDocuments2::OnAfter*` método para notificar el entorno que la operación ha finalizado. El proyecto debe llamar a los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz para todos los archivos (por ejemplo, archivos especiales) y no solo los archivos principales. Las llamadas de archivos son obligatorias, pero las llamadas de directorio son opcionales. Si el proyecto tiene información de directorio, a continuación, debe llamar a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos, pero si no tiene esta información, el entorno deducirá información del directorio.

 El proyecto no debe llamar a los métodos de `IVsTrackProjectDocuments2` al proyecto, abrir o cerrar. Los agentes de escucha que desean que esta información en el inicio pueden esperar a que el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> eventos e iterar a través de la solución para encontrar la información que necesitan. En el apagado, esta información no es necesaria. `IVsTrackProjectDocuments2` se proporciona desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Para cada agregar, cambiar el nombre y acción de eliminación, hay un `OnQuery*` método y un `OnAfter*` método. Llame a la `OnQuery*` método para pedir permiso para agregar, cambiar el nombre o quite el archivo o directorio. Llame a la `OnAfter*` método después de que el archivo o directorio ha se han agregado, cambiado o quitado y el estado del proyecto refleja el estado nueva.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)