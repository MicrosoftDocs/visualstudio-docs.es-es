---
title: 'Cómo: usar la administración de deshacer vinculada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842591"
---
# <a name="how-to-use-linked-undo-management"></a>Cómo: Usar la administración vinculada de la fase de reversión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La operación deshacer vinculada permite al usuario deshacer simultáneamente las mismas modificaciones en varios archivos. Por ejemplo, los cambios de texto simultáneos en varios archivos de programa, como un archivo de encabezado y un archivo Visual C++, es una transacción vinculada de deshacer. La funcionalidad de deshacer vinculada está integrada en la implementación del entorno del administrador de deshacer y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite manipular esta funcionalidad. La operación deshacer vinculada se implementa mediante una unidad primaria de deshacer que puede vincular las pilas de deshacer independientes para que se traten como una sola unidad de deshacer. El procedimiento para utilizar la operación de deshacer vinculada se detalla en la sección siguiente.  
  
### <a name="to-use-linked-undo"></a>Para usar la operación de deshacer vinculada  
  
1. Llame a `QueryService` en `SVsLinkedUndoManager` para obtener un puntero a `IVsLinkedUndoTransactionManager` .  
  
2. Cree la unidad primaria de deshacer vinculada principal mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Esto establece el punto de partida para un conjunto de pilas de deshacer que se van a agrupar en pilas de deshacer vinculadas. En el `OpenLinkedUndo` método también tendrá que especificar si desea que la operación de deshacer vinculada sea estricta o no estricta. El comportamiento de deshacer vinculado no estricto significa que algunos de los documentos con los elementos del mismo nivel de deshacer vinculados pueden cerrarse y seguir dejando los demás elementos del mismo nivel de deshacer vinculados en sus pilas. El comportamiento de deshacer vinculado estricto especifica que todas las pilas relacionadas de deshacer vinculadas deben deshacerse juntas o no. Agregue las sucesivas pilas de deshacer vinculadas mediante una llamada al método [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> a para revertir todas las unidades de deshacer vinculadas como una.  
  
    > [!NOTE]
    > Para implementar administración de deshacer vinculada en un editor, agregue administración de deshacer. Para obtener más información sobre la implementación de la administración de deshacer vinculada, vea [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)
