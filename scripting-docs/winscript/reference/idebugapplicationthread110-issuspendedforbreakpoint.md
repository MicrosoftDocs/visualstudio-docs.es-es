---
title: IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82b8957ae9f2b6674af7addf2239c745115e4e3f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440523"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Determina si [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) se ha llamado en este subproceso y no se ha completado.  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 (interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfIsSuspended`  
 [out] `true` si el subproceso está suspendido en caso contrario, un punto de interrupción, `false`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread110 (Interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md)