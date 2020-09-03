---
title: Consultar editar consulta guardar (VSPackage de control de código fuente) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148888"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar/guardar consulta (VSPackage de control de código fuente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] los editores pueden difundir eventos de modificación de consultas de edición de consulta (QEQS). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] El código auxiliar de control de código fuente implementa el servicio QEQS, de modo que es el destinatario de los eventos QEQS. A continuación, estos eventos se delegan en el VSPackage de control de código fuente activo actualmente. El VSPackage de control de código fuente activo implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y sus métodos. `IVsQueryEditQuerySave2`Normalmente se llama a los métodos de la interfaz inmediatamente antes de que un documento se edite por primera vez y inmediatamente antes de que se guarde un documento.  
  
## <a name="queryeditquerysave-events"></a>Eventos QueryEditQuerySave  
 El VSPackage de control de código fuente debe controlar los eventos QEQS implementando la `IVsQueryEditQuerySave2` interfaz y los métodos necesarios. A continuación se muestra una breve descripción de los dos métodos que el VSPackage debe implementar como mínimo. La implementación real debe estar de acuerdo con la lógica del modelo de control de código fuente.  
  
### <a name="queryeditfiles-method"></a>Método QueryEditFiles  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Se llama a cuando cualquier proyecto o editor desea modificar un archivo. Idealmente, se llama a este método *antes* de que se modifique el archivo y cuando se guarda un archivo. Cuando se invoca, el `IVsQueryEditQuerySave2::QueryEditFiles` método comprueba si los archivos especificados están bajo control de código fuente, si es necesario desprotegerlos y si se pueden volver a cargar. Si las circunstancias impiden que los archivos se puedan editar, el `IVsQueryEditQuerySave2::QueryEditFiles` método indica al programa que realiza la llamada que cancele la edición. También es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método solo realiza una acción si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.  
  
 El método se comporta de manera transaccional; es decir, si se cancela la edición en un solo archivo, la edición se cancela para todos los archivos. Por el contrario, si se permite la edición, se permite para todos los archivos. Si este método permite la edición una vez para un conjunto determinado de archivos, siempre debe permitir la edición en llamadas posteriores para el mismo conjunto de archivos. El bucle allow-Edit continúa hasta que se cierran, guardan y recargan los archivos. hasta que cambien sus atributos (propiedades); o hasta que se cambie el paquete de control de código fuente. Entre los casos que se deben tener en cuenta al implementar el `IVsQueryEditQuerySave2::QueryEditFiles` método se incluyen varios archivos, archivos especiales, cancelación de usuario y ediciones en memoria.  
  
### <a name="querysavefiles-method"></a>Método QuerySaveFiles  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Se llama a cuando cualquier proyecto o editor necesita guardar un conjunto de archivos. Cuando se invoca, el `IVsQueryEditQuerySave2::QuerySaveFiles` método comprueba si los archivos especificados son de solo lectura y si están bajo control de código fuente. Si los archivos deben desprotegerse, la llamada se delega en el paquete de control de código fuente. Si las circunstancias impiden que los archivos se guarden, el `IVsQueryEditQuerySave2::QuerySaveFiles` método debe indicar al editor que cancele la guardado. Al igual que con el `IVsQueryEditQuerySave2::QueryEditFiles` método, es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método solo realiza una acción si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.  
  
 Este método debe comportarse de manera transaccional; es decir, si se cancela la guardado en un único archivo, se cancela la guardado de todos los archivos. Por el contrario, si se permite el guardado, debe permitirse para todos los archivos. Como con el `IVsQueryEditQuerySave2::QueryEditFiles` método, los casos que se deben tener en cuenta al implementar el `IVsQueryEditQuerySave2::QuerySaveFiles` método incluyen varios archivos, archivos especiales, cancelación del usuario y ediciones en memoria.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
