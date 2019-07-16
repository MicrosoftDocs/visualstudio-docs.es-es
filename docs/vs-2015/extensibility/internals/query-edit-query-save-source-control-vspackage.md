---
title: Editar consulta guardar (VSPackage de Control de código fuente) de consulta | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad0cf7c3e1d3269dbe7ebee051cc32e2e8531ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148888"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar/guardar consulta (VSPackage de control de código fuente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] los editores pueden difundir eventos de consulta Editar consulta guardar (QEQS). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Código auxiliar de Control de código fuente se implementa el servicio QEQS, para que sea el destinatario de los eventos QEQS. Estos eventos, a continuación, se delegan al VSPackage de control de origen actualmente activo. El control de origen activo VSPackage implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y sus métodos. Los métodos de la `IVsQueryEditQuerySave2` interfaz normalmente se llama justo antes de que se modifica un documento por primera vez e inmediatamente antes de que se guarda un documento.  
  
## <a name="queryeditquerysave-events"></a>Eventos QueryEditQuerySave  
 El control de código fuente VSPackage debe controlar los eventos QEQS implementando la `IVsQueryEditQuerySave2` interfaz y los métodos necesarios. A continuación es una breve descripción de los dos métodos que VSPackage debe implementar como mínimo. La implementación real debe ser según la lógica del modelo de control de código fuente.  
  
### <a name="queryeditfiles-method"></a>Método QueryEditFiles  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> se llama cuando cualquier editor o proyecto desea modificar un archivo. Idealmente, este método se llama *antes* se modifica el archivo y cuando se guarda un archivo. Cuando se invoca, el `IVsQueryEditQuerySave2::QueryEditFiles` método comprueba si los archivos indicados están bajo control de código fuente, si necesitan que se desprotegerán y si puede recargarse. Si circunstancias impide los archivos editables, el `IVsQueryEditQuerySave2::QueryEditFiles` método indica al programa que realiza la llamada para cancelar la edición. También es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método sólo ejecuta si no hace ninguna interfaz de usuario que aparezca. Si la interfaz de usuario es inevitable, debe devolverse una marca para indicar el problema.  
  
 El método se comporta de forma transaccional. es decir, si se cancela la edición en un único archivo, se ha cancelado la edición para todos los archivos. Por el contrario, si se permite la edición, se permite para todos los archivos. Si este método permite la edición una vez para un determinado conjunto de archivos, siempre debe permitir la edición en las llamadas posteriores para el mismo conjunto de archivos. Permitir edición bucle continúa hasta que se cierra, se guardan y se vuelve a cargar; los archivos hasta que cambiarán sus atributos (propiedades); o bien, hasta que se modifica el paquete de control de código fuente. Los casos en cuenta al implementar el `IVsQueryEditQuerySave2::QueryEditFiles` método incluyen varios archivos, archivos especiales, Cancelar de usuario y las ediciones en memoria.  
  
### <a name="querysavefiles-method"></a>Método QuerySaveFiles  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> se llama cuando cualquier editor o proyecto debe guardar un conjunto de archivos. Cuando se invoca, el `IVsQueryEditQuerySave2::QuerySaveFiles` método comprueba si los archivos indicados son de solo lectura y si están bajo control de código fuente. Si necesitan desproteger los archivos, la llamada se delega en el paquete de control de código fuente. Si las circunstancias, evitar que los archivos que se guarden, el `IVsQueryEditQuerySave2::QuerySaveFiles` método debe indicar el editor para cancelar la operación de guardar. Igual que con el `IVsQueryEditQuerySave2::QueryEditFiles` método, es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método sólo ejecuta si no hace ninguna interfaz de usuario que aparezca. Si la interfaz de usuario es inevitable, debe devolverse una marca para indicar el problema.  
  
 Este método debe comportarse de forma transaccional. es decir, si se cancela la operación de guardar en un único archivo, se ha cancelado la operación de guardar para todos los archivos. Por el contrario, si se permite la operación de guardar, debe permitir para todos los archivos. Igual que con el `IVsQueryEditQuerySave2::QueryEditFiles` método, los casos en cuenta al implementar el `IVsQueryEditQuerySave2::QuerySaveFiles` método incluyen varios archivos, archivos especiales, Cancelar de usuario y las ediciones en memoria.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
