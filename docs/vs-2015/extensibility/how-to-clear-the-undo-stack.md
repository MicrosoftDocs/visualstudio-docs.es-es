---
title: Filtrar Borrar la pila de deshacer | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e45ec665b75be99781495bc5f2407c30c5f7e12a
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "59002124"
---
# <a name="how-to-clear-the-undo-stack"></a>Filtrar Borrar la pila de deshacer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El siguiente procedimiento a continuación explica cómo borrar la pila de deshacer.  
  
### <a name="to-clear-the-undo-stack"></a>Para borrar la pila de deshacer  
  
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
 [Cómo: Implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)
