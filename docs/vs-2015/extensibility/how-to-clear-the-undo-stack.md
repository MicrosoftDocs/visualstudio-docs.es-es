---
title: 'Cómo: borrar la pila de deshacer | Microsoft Docs'
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
ms.openlocfilehash: db77f93fd7f6af16b5358b75b6ffcd5927430653
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549174"
---
# <a name="how-to-clear-the-undo-stack"></a>Cómo: Borrar la pila de la fase de reversión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el siguiente procedimiento se explica cómo borrar la pila de deshacer.  
  
### <a name="to-clear-the-undo-stack"></a>Para borrar la pila de deshacer  
  
1. Para borrar la pila de deshacer, use el método [IOleUndoManager::D iscardfrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) . El siguiente es un ejemplo de esto:  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)
