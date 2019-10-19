---
title: 'Idebugapplicationthreadevents110 (:: OnSuspendForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d73d7769dd48889a75da63da64be1d2977a088
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573342"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Determina si el subproceso se ha suspendido completamente para un punto de interrupción y aún no se ha reanudado la ejecución normal.  
  
> [!IMPORTANT]
> La [interfaz idebugapplicationthreadevents110 (](../../winscript/reference/idebugapplicationthreadevents110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no tiene parámetros.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThreadEvents110 (Interfaz)](../../winscript/reference/idebugapplicationthreadevents110-interface.md)