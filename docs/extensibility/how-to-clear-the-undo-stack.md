---
title: "C&#243;mo: borrar la pila de deshacer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - borrar la pila de deshacer"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;mo: borrar la pila de deshacer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El siguiente procedimiento siguiente explica cómo borrar la pila de deshacer.  
  
### Para borrar la pila de deshacer  
  
1.  Para borrar el uso de la pila de deshacer el método de [IOleUndoManager:: DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) .  A continuación se muestra un ejemplo de esto:  
  
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
  
## Vea también  
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)