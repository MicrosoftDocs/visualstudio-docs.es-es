---
title: Detalles de la configuración de Control de código fuente ( Source Control) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705291"
---
# <a name="source-control-configuration-details"></a>Detalles de configuración del control de código fuente
Para implementar el control de código fuente, debe configurar correctamente el sistema de proyectos o el editor para hacer lo siguiente:

- Solicitar permiso para la transición al estado cambiado

- Solicitar permiso para guardar un archivo

- Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos en el proyecto

## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permiso para la transición al estado cambiado
 Un proyecto o editor debe solicitar permiso para pasar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>al estado modificado (sucio) llamando a . Cada editor que <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> debe llamar y recibir aprobación para `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>cambiar el documento del entorno antes de devolver para . Un proyecto es esencialmente un editor para un archivo de proyecto y, como resultado, tiene la misma responsabilidad de implementar el seguimiento de estado modificado para el archivo de proyecto que un editor de texto para sus archivos. El entorno controla el estado modificado de la solución, pero debe controlar el estado modificado de cualquier objeto al que hace referencia la solución, pero no almacena, como un archivo de proyecto o sus elementos. En general, si el proyecto o editor es responsable de administrar la persistencia de un elemento, es responsable de implementar el seguimiento de estado modificado.

 En respuesta `IVsQueryEditQuerySave2::QueryEditFiles` a la llamada, el entorno puede hacer lo siguiente:

- Rechazar la llamada a cambiar, en cuyo caso el editor o proyecto debe permanecer en el estado sin cambios (limpio).

- Indique que se deben volver a cargar los datos del documento. Para un proyecto, el entorno volverá a cargar los datos del proyecto. Un editor debe volver a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> cargar los datos desde el disco a través de su implementación. En cualquier caso, el contexto del proyecto o del editor puede cambiar cuando se vuelven a cargar los datos.

  Es una tarea compleja y difícil `IVsQueryEditQuerySave2::QueryEditFiles` reacondicionar las llamadas adecuadas a una base de código existente. Como resultado, estas llamadas deben integrarse durante la creación del proyecto o editor.

## <a name="request-permission-to-save-a-file"></a>Solicitar permiso para guardar un archivo
 Antes de que un proyecto o editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>guarde un archivo, debe llamar o . Para los archivos de proyecto, la solución completa automáticamente estas llamadas, que sabe cuándo guardar un archivo de proyecto. Los editores son responsables de realizar `IVsPersistDocData2` estas llamadas a menos que la implementación del editor de use la función <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>auxiliar . Si el editor `IVsPersistDocData2` se implementa de esta `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` manera, la llamada o se realiza para usted.

> [!NOTE]
> Realice siempre estas llamadas de forma preventiva, es decir, en un momento en que el editor puede recibir una cancelación.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permiso para agregar, quitar o cambiar el nombre de los archivos en el proyecto
 Para que un proyecto pueda agregar, cambiar el nombre o `IVsTrackProjectDocuments2::OnQuery*` quitar un archivo o directorio, debe llamar al método adecuado para solicitar permiso del entorno. Si se concede permiso, el proyecto debe completar la `IVsTrackProjectDocuments2::OnAfter*` operación y, a continuación, llamar al método adecuado para notificar al entorno que la operación se ha completado. El proyecto debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> a los métodos de la interfaz para todos los archivos (por ejemplo, archivos especiales) y no solo para los archivos primarios. Las llamadas a archivos son obligatorias, pero las llamadas de directorio son opcionales. Si el proyecto tiene información de directorio, debe llamar a los métodos adecuados, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> pero si no tiene esta información, el entorno deducirá la información del directorio.

 El proyecto no debe `IVsTrackProjectDocuments2` llamar a los métodos de at project open o close. Los agentes de escucha que desean <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> esta información en el inicio pueden esperar el evento e iterar a través de la solución para encontrar la información que necesitan. Al apagar, esta información no es necesaria. `IVsTrackProjectDocuments2`se proporciona <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>desde el .

 Para cada acción de agregar, cambiar `OnQuery*` el nombre `OnAfter*` y quitar, hay un método y un método. Llame `OnQuery*` al método para solicitar permiso para agregar, cambiar el nombre o quitar el archivo o directorio. Llame `OnAfter*` al método después de que el archivo o directorio se haya agregado, cambiado de nombre o quitado y el estado del proyecto refleje el nuevo estado.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
