---
title: 'Cómo: usar la administración de la fase de reversión vinculado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 255ad8de79b13a74816b2abd28281ac5de6f1932
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370567"
---
# <a name="how-to-use-linked-undo-management"></a>Cómo: usar vinculada de deshacer la administración
Fase de reversión vinculado permite al usuario simultáneamente deshacer las modificaciones mismas en varios archivos. Por ejemplo, los cambios de texto simultánea en varios archivos de programa, como un archivo de encabezado y un archivo de Visual C++, es una transacción vinculada de deshacer. Capacidad de deshacer vinculada está integrada en la implementación del entorno de que el Administrador de deshacer y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite manipular esta capacidad. Acción de deshacer vinculada se implementa mediante una unidad de deshacer primaria que se puede vincular las pilas de deshacer independiente juntos a tratarse como una unidad de deshacer única. El procedimiento para utilizar vinculada de deshacer se detalla en la sección siguiente.  
  
## <a name="to-use-linked-undo"></a>Para usar la acción de deshacer vinculada  
  
1.  Llame a `QueryService` en `SVsLinkedUndoManager` para obtener un puntero a `IVsLinkedUndoTransactionManager`.  
  
2.  Crear la unidad de deshacer vinculada principal inicial mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Esto establece el punto de partida para un conjunto de las pilas de deshacer se agrupan en las pilas de deshacer vinculada. En el `OpenLinkedUndo` método también deberá especificar si desea que la operación de deshacer vinculada ser estricta o no es estricta. Comportamiento de deshacer vinculada no estricta significa que algunos de los documentos con la fase de reversión vinculado del mismo nivel pueden cerrar y dejar el otro vinculado elementos del mismo nivel en sus pilas de deshacer. Comportamiento de deshacer vinculada estricta especifica que todas las pilas de deshacer vinculada del mismo nivel que se deshagan conjuntamente o no. Agregar posteriores vinculado pilas de deshacer llamando [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) método.  
  
3.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> para implementar todas las unidades de deshacer vinculada como uno.  
  
    > [!NOTE]
    >  Para implementar la administración de la fase de reversión vinculado en un editor, agregue administración de deshacer. Para obtener más información sobre la implementación de administración de la fase de reversión vinculado, vea [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)