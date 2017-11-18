---
title: "Consultar Editar consulta guardar (VSPackage de Control de código fuente) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0aeb24f52b1b6b719e81dcd1a9bd93bd5822f8e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar consulta guardar (VSPackage de Control de código fuente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]editores pueden difundir eventos de consulta Editar consulta guardar (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Código auxiliar de Control de código fuente se implementa el servicio QEQS, para que sea el destinatario de los eventos QEQS. Estos eventos se delegan, a continuación, en el control de origen activo actualmente VSPackage. El control de origen activo VSPackage implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y sus métodos. Los métodos de la `IVsQueryEditQuerySave2` interfaz se suelen denominar simplemente inmediatamente antes de que se modifica un documento por primera vez, e inmediatamente antes de que se guarda un documento.  
  
## <a name="queryeditquerysave-events"></a>Eventos de QueryEditQuerySave  
 El control de código fuente VSPackage debe controlar los eventos QEQS implementando la `IVsQueryEditQuerySave2` interfaz y los métodos necesarios. A continuación se muestra una breve descripción de los dos métodos que debe implementar el VSPackage como mínimo. La implementación real debe ser según la lógica del modelo de control de código fuente.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles (método)  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> se llama cuando se desea modificar un archivo de cualquier proyecto o el editor. Idealmente, se llama a este método *antes de* se modifica el archivo y cuando se guarda un archivo. Cuando se invoca, el `IVsQueryEditQuerySave2::QueryEditFiles` método comprueba si los archivos determinados están bajo control de código fuente, si necesitan que se extraiga del repositorio y si puede volver a cargar. Si circunstancias que impiden que los archivos que se puede editar, el `IVsQueryEditQuerySave2::QueryEditFiles` método indica al programa que realiza la llamada para cancelar la edición. También es posible que el autor de la llamada especificar un modo de invocación. En el modo "silencioso", este método realiza la acción solo si no hace que cualquier interfaz de usuario que aparezca. Si es inevitable la interfaz de usuario, se debe devolver una marca para indicar el problema.  
  
 El método se comporta de forma transaccional; es decir, si se cancela la edición en un único archivo, se cancela la edición de todos los archivos. Por el contrario, si se permite la edición, se permite para todos los archivos. Si este método permite la edición de una vez para un conjunto determinado de archivos, siempre debe permitir la edición en las llamadas posteriores para el mismo conjunto de archivos. Permitir edición bucle continúa hasta que los archivos se cierra, se guardan y se vuelven a cargar; hasta que cambiarán sus atributos (propiedades); o bien, hasta que se cambie el paquete de control de código fuente. Para tener en cuenta en la implementación de los casos el `IVsQueryEditQuerySave2::QueryEditFiles` método incluyen varios archivos, archivos especiales, Cancelar de usuario y tareas de edición en memoria.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles (método)  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> llama cuando cualquier editor o el proyecto se debe guardar un conjunto de archivos. Cuando se invoca, el `IVsQueryEditQuerySave2::QuerySaveFiles` método comprueba si los archivos determinados son de solo lectura y si ya están bajo el control de código fuente. Si es necesario desproteger los archivos, la llamada se delega en el paquete de control de código fuente. Si hay circunstancias impiden que los archivos se guarda, la `IVsQueryEditQuerySave2::QuerySaveFiles` método debe indicarle al editor para cancelar la operación de guardar. Al igual que con el `IVsQueryEditQuerySave2::QueryEditFiles` método, es posible que el autor de la llamada especificar un modo de invocación. En el modo "silencioso", este método realiza la acción solo si no hace que cualquier interfaz de usuario que aparezca. Si es inevitable la interfaz de usuario, se debe devolver una marca para indicar el problema.  
  
 Este método debe comportarse de forma transaccional; es decir, si se cancela la operación de guardar en un único archivo, se cancela la operación de guardar para todos los archivos. Por el contrario, si se permite la operación de guardar, debe permitirse para todos los archivos. Al igual que con la `IVsQueryEditQuerySave2::QueryEditFiles` /método siguiente, los casos en cuenta al implementar la `IVsQueryEditQuerySave2::QuerySaveFiles` método incluyen varios archivos, archivos especiales, Cancelar de usuario y tareas de edición en memoria.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>