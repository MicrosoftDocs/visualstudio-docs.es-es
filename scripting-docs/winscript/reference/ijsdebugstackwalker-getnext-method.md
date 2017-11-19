---
title: "Ijsdebugstackwalker:: GetNext (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 695bb6cecc2a27565dce21b4a965ad08d90d7be7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalkergetnext-method"></a>IJsDebugStackWalker::GetNext (Método)
Obtiene el siguiente fotograma.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppFrame`  
 [out] Objeto que representa el marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_OUTSIDE_OF_VM cuando no hay ningún más marcos de pila que hay que enumerar  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugStackWalker (Interfaz)](../../winscript/reference/ijsdebugstackwalker-interface.md)