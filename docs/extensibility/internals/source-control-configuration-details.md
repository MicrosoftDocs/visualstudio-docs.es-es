---
title: Detalles de configuración del control de código fuente | Microsoft Docs
description: Obtenga información sobre cómo implementar el control de código fuente para un tipo de proyecto en Visual Studio, lo que implica configurar el sistema del proyecto o el editor para solicitar permisos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a3a2f33fcbb94d1e863daf69b8561f7bad4f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846509"
---
# <a name="source-control-configuration-details"></a>Detalles de configuración del control de código fuente
Para implementar el control de código fuente, debe configurar correctamente el sistema del proyecto o el editor para hacer lo siguiente:

- Solicitar permiso para realizar la transición al estado cambiado

- Solicitar permiso para guardar un archivo

- Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos del proyecto

## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permiso para realizar la transición al estado cambiado
 Un proyecto o editor debe solicitar permiso para realizar la transición al estado cambiado (modificado) mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y recibir la aprobación para cambiar el documento del entorno antes de que se devuelva `True` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Un proyecto es esencialmente un editor para un archivo de proyecto y, como resultado, tiene la misma responsabilidad para implementar el seguimiento de estado cambiado para el archivo de proyecto como lo hace un editor de texto para sus archivos. El entorno controla el estado cambiado de la solución, pero debe controlar el estado cambiado de cualquier objeto al que la solución hace referencia pero no almacena, como un archivo de proyecto o sus elementos. En general, si el proyecto o el editor es responsable de administrar la persistencia de un elemento, es responsable de implementar el seguimiento de estado cambiado.

 En respuesta a la `IVsQueryEditQuerySave2::QueryEditFiles` llamada, el entorno puede hacer lo siguiente:

- Rechace la llamada a Change, en cuyo caso el editor o el proyecto deben permanecer en el estado Unchanged (Clean).

- Indica que los datos del documento se deben recargar. Para un proyecto de, el entorno volverá a cargar los datos del proyecto. Un editor debe volver a cargar los datos del disco a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementación. En cualquier caso, el contexto del proyecto o editor puede cambiar cuando se recargan los datos.

  Es una tarea compleja y difícil de convertir `IVsQueryEditQuerySave2::QueryEditFiles` las llamadas adecuadas en una base de código existente. Como resultado, estas llamadas se deben integrar durante la creación del proyecto o editor.

## <a name="request-permission-to-save-a-file"></a>Solicitar permiso para guardar un archivo
 Antes de que un proyecto o editor guarde un archivo, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . En el caso de los archivos de proyecto, estas llamadas se completan automáticamente mediante la solución, lo que sabe cuándo se debe guardar un archivo de proyecto. Los editores son responsables de realizar estas llamadas a menos que la implementación del editor de `IVsPersistDocData2` Utilice la función auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Si el editor implementa `IVsPersistDocData2` de esta manera, la llamada a `IVsQueryEditQuerySave2::QuerySaveFile` o `IVsQueryEditQuerySave2::QuerySaveFiles` se realiza automáticamente.

> [!NOTE]
> Realice estas llamadas siempre de forma preferente, es decir, cada vez que el editor pueda recibir una cancelación.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos del proyecto
 Para que un proyecto pueda agregar, cambiar de nombre o quitar un archivo o un directorio, debe llamar al `IVsTrackProjectDocuments2::OnQuery*` método adecuado para solicitar permiso desde el entorno. Si se concede el permiso, el proyecto debe completar la operación y, a continuación, llamar al `IVsTrackProjectDocuments2::OnAfter*` método adecuado para notificar al entorno que la operación se ha completado. El proyecto debe llamar a los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz para todos los archivos (por ejemplo, archivos especiales) y no solo los archivos primarios. Las llamadas de archivo son obligatorias, pero las llamadas de directorio son opcionales. Si el proyecto tiene información de directorio, debe llamar a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos adecuados, pero si no tiene esta información, el entorno deducirá la información de directorio.

 El proyecto no debe llamar a los métodos de `IVsTrackProjectDocuments2` en el proyecto abrir o cerrar. Los agentes de escucha que desean esta información en el inicio pueden esperar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> evento y recorrer en iteración la solución para encontrar la información que necesitan. En el apagado, esta información no es necesaria. `IVsTrackProjectDocuments2` se proporciona desde <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Para cada acción de agregar, cambiar nombre y quitar, hay un `OnQuery*` método y un `OnAfter*` método. Llame al `OnQuery*` método para solicitar permiso para agregar, cambiar el nombre o quitar el archivo o directorio. Llame al `OnAfter*` método una vez agregado, cambiado de nombre o quitado el archivo o directorio y el estado del proyecto refleja el nuevo estado.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
