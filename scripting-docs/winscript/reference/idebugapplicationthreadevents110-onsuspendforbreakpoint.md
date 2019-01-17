---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a3ce1510ad9e7b4560a7aaafb8d65d5b0e6143cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349642"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Determina si el subproceso ha suspendido por completo para un punto de interrupción y aún no ha reanudado la ejecución normal.  
  
> [!IMPORTANT]
>  [IDebugApplicationThreadEvents110 (interfaz)](../../winscript/reference/idebugapplicationthreadevents110-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no tiene parámetros.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThreadEvents110 (Interfaz)](../../winscript/reference/idebugapplicationthreadevents110-interface.md)