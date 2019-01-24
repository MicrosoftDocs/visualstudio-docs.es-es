---
title: Procedimiento Implementar la administración de deshacer | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 005b321921003e11f9204616727e0b06b85e5c3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915661"
---
# <a name="how-to-implement-undo-management"></a>Procedimiento Implementar la administración de deshacer
La interfaz principal que se usa para la administración de deshacer es <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, que es implementado por el entorno. Para admitir la administración de deshacer, implementar unidades de deshacer independiente (es decir, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, que puede contener varios pasos individuales.  
  
 Cómo implementar la administración de deshacer varía en función de si el editor admite varias vistas o no. Los procedimientos para cada implementación se detallan en las secciones siguientes.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casos donde un editor es compatible con una sola vista  
 En este escenario, el editor no admite varias vistas. Hay solo un editor y un documento y permiten deshacer. Use el procedimiento siguiente para implementar la administración de deshacer.  
  
### <a name="to-support-undo-management-for-a-single-view-editor"></a>Para admitir la administración de la fase de reversión para un editor de vista única  
  
1.  Llame a `QueryInterface` en el `IServiceProvider` interfaz en el marco de ventana para `IOleUndoManager`, desde el objeto de vista de documento para obtener acceso al administrador de deshacer (`IID_IOLEUndoManager`).  
  
2.  Cuando una vista está ubicada en un marco de ventana, obtiene un puntero de sitio, que puede usar para llamar a `QueryInterface` para `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casos donde un editor admite varias vistas  
 Si dispone de separación de documento y vista, hay administrador de deshacer normalmente, un asociado con el propio documento. Todas las unidades de deshacer se colocan en el Administrador de deshacer asociado al objeto de datos de documento.  
  
 En lugar de la vista de consulta para el Administrador de deshacer, de los cuales hay uno para cada vista, los datos del documento de objeto llama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear una instancia del Administrador de deshacer, especificando un identificador de clase de CLSID_OLEUndoManager. El identificador de clase se define en el *OCUNDOID.h* archivo.  
  
 Cuando se usa <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear su propia instancia del Administrador de deshacer, use el siguiente procedimiento para enlazar el Administrador de deshacer en el entorno.  
  
### <a name="to-hook-your-undo-manager-into-the-environment"></a>Para enlazar el Administrador de deshacer en el entorno  
  
1. Llame a `QueryInterface` en el objeto devuelto desde <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> para `IID_IOleUndoManager`. Store el puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IOleCommandTarget`. Store el puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3. Retransmisión su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> llama a almacenado `IOleCommandTarget` interfaz para los siguientes comandos de StandardCommandSet97:  
  
   -   cmdidUndo  
  
   -   cmdidMultiLevelUndo  
  
   -   cmdidRedo  
  
   -   cmdidMultiLevelRedo  
  
   -   cmdidMultiLevelUndoList  
  
   -   cmdidMultiLevelRedoList  
  
4. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IVsChangeTrackingUndoManager`. Store el puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
    Use el puntero para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> para llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> métodos.  
  
5. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IVsLinkCapableUndoManager`.  
  
6. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con el documento, que debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfaz. Cuando se cierra el documento, llame a `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7. Cuando se cierra el documento, llame a `QueryInterface` en el Administrador de deshacer para `IID_IVsLifetimeControlledObject`.  
  
8. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Cuando se realizan cambios en el documento, llame a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> en el Administrador de con un `OleUndoUnit` clase. El <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> método mantiene una referencia al objeto, por lo general, liberarlo inmediatamente después del <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
   La `OleUndoManager` clase representa una instancia de la pila de deshacer única. Por lo tanto, hay un objeto de administrador de deshacer cada entidad de datos está realizando un seguimiento para deshacer o rehacer.  
  
> [!NOTE]
>  Mientras que el objeto de administrador de deshacer es utilizado por el editor de texto, es un componente general que no tiene proporciona compatibilidad específica del editor de texto. Si desea admitir varios niveles de deshacer o rehacer, puede utilizar este objeto para hacerlo.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Cómo: Borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md)