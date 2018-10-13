---
title: 'Cómo: borrar la pila de deshacer | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d445b4ce79dc2f048ee95c1a356863f1ed524dad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210293"
---
# <a name="how-to-clear-the-undo-stack"></a>Cómo: borrar la pila de deshacer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El siguiente procedimiento a continuación explica cómo borrar la pila de deshacer.  
  
### <a name="to-clear-the-undo-stack"></a>Para borrar la pila de deshacer  
  
1.  Para borrar el uso de la pila de deshacer la [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) método. Este es un ejemplo de esto:  
  
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
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)

