---
title: 'Cómo: implementar la administración de deshacer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843219"
---
# <a name="how-to-implement-undo-management"></a>Cómo: Implementar la administración de la fase de reversión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La interfaz principal que se usa para la administración de deshacer es <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , que es implementada por el entorno. Para admitir la administración de deshacer, implemente unidades de deshacer independientes (es decir, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> , que puede contener varios pasos individuales.  
  
 La forma de implementar la administración de deshacer varía en función de si el editor admite o no varias vistas. Los procedimientos para cada implementación se detallan en las secciones siguientes.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casos en los que un editor admite una sola vista  
 En este escenario, el editor no admite varias vistas. Solo hay un editor y un documento, y admiten la operación de deshacer. Utilice el procedimiento siguiente para implementar la administración de deshacer.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Para admitir la administración de deshacer para un editor de vista única  
  
1. Llame a `QueryInterface` en la `IServiceProvider` interfaz en el marco de ventana de `IOleUndoManager` , desde el objeto de vista de documento para tener acceso al administrador de deshacer ( `IID_IOLEUndoManager` ).  
  
2. Cuando una vista se encuentra en un marco de ventana, obtiene un puntero de sitio, que puede usar para llamar a `QueryInterface` para `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casos en los que un editor admite varias vistas  
 Si tiene separación de documentos y vistas, normalmente hay un administrador de deshacer asociado al propio documento. Todas las unidades de deshacer se colocan en un administrador de deshacer asociado al objeto de datos del documento.  
  
 En lugar de ver la consulta para el administrador de deshacer, de la que hay una para cada vista, el objeto de datos del documento llama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> a para crear una instancia del administrador de deshacer, especificando un identificador de clase de CLSID_OLEUndoManager. El identificador de clase se define en el archivo OCUNDOID. h.  
  
 Al usar <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear su propia instancia del administrador de deshacer, utilice el procedimiento siguiente para enlazar el administrador de deshacer en el entorno.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Para enlazar el administrador de deshacer en el entorno  
  
1. Llame a `QueryInterface` en el objeto devuelto <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> por para `IID_IOleUndoManager` . Almacene el puntero en <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IOleCommandTarget` . Almacene el puntero en <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Retransmita su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> llama a la interfaz almacenada `IOleCommandTarget` para los siguientes comandos de StandardCommandSet97:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IVsChangeTrackingUndoManager` . Almacene el puntero en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Utilice el puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> para llamar a los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> métodos, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Llame a `QueryInterface` en `IOleUndoManager` para `IID_IVsLinkCapableUndoManager` .  
  
6. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con el documento, que también debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfaz. Cuando el documento esté cerrado, llame a `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Cuando se cierre el documento, llame a `QueryInterface` en el administrador de deshacer para `IID_IVsLifetimeControlledObject` .  
  
8. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Cuando se realicen cambios en el documento, llame a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> en el administrador con una `OleUndoUnit` clase. El <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> método mantiene una referencia al objeto, por lo que generalmente se libera justo después de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   La `OleUndoManager` clase representa una única instancia de la pila de deshacer. Por lo tanto, hay un objeto de administrador de deshacer por cada entidad de datos cuyo seguimiento se realiza para deshacer o rehacer.  
  
> [!NOTE]
> Aunque el editor de texto utiliza el objeto de administrador de deshacer, es un componente general que no tiene ninguna compatibilidad específica para el editor de texto. Si desea admitir la operación de deshacer o rehacer de varios niveles, puede utilizar este objeto para hacerlo.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Cómo: Borrar la pila de la fase de reversión](../extensibility/how-to-clear-the-undo-stack.md)
