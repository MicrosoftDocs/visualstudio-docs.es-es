---
title: Método Ijsdebugbreakpoint | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24584d0e9708dab4879ceb26f0af5e142936210a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583248"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable (Método)
Deshabilita el punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_UNEXPECTED si se llama en un punto de interrupción eliminado. Devuelve S_FALSE si se llama en un punto de interrupción ya deshabilitado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugBreakPoint (Interfaz)](../../winscript/reference/ijsdebugbreakpoint-interface.md)