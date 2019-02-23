---
title: Filtrar Borrar la pila de deshacer | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb1b1c1d79bab15baa8e8afcab719b3081e7265b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712104"
---
# <a name="how-to-clear-the-undo-stack"></a>Filtrar Borrar la pila de deshacer
El siguiente procedimiento a continuación explica cómo borrar la pila de deshacer.

## <a name="to-clear-the-undo-stack"></a>Para borrar la pila de deshacer

1.  Para borrar el uso de la pila de deshacer la [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) método. Este es un ejemplo de esto:

    ```
    HRESULT CCmdWindow::ClearUndoStack()
    {
      HRESULT hr = S_OK;

      if (m_pUndoMgr == NULL)
        {
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));
        ASSERT(m_pUndoMgr != NULL, "",;);
        }

      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));

    Error:
      return hr;
    }
    ```

## <a name="see-also"></a>Vea también
- [Cómo: Implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)