---
title: 'IJsDebugProcess:: Createstackwalker ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573838"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker (Método)
Método de generador para el rastreador de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 de IDENTIFICADOR del subproceso.  
  
 `ppStackWalker`  
 enuncia Nuevo objeto de rastreador de pila.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_UNKNOWN_THREAD si el subproceso no tiene JavaScript en él. Solo se puede llamar a este método mientras se detiene el proceso de destino.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProcess (Interfaz)](../../winscript/reference/ijsdebugprocess-interface.md)