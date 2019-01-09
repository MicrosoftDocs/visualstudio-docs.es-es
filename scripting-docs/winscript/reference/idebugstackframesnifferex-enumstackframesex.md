---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c34ce267113ae5576a8b3bdca9ac34d4abc00f7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086976"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Devuelve un enumerador de marcos de pila del subproceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSpMin`  
 [in] El límite inferior de dirección para enumerar los marcos de pila.  
  
 `ppedsf`  
 [out] Enumerador de marcos de pila del subproceso actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El enumerador del marco de pila devuelve los marcos desde la parte superior de la pila, con el marco insertado más recientemente. El enumerador contiene marcos de pila solo con direcciones mayores o iguales que `dwSpMin`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrameSnifferEx (Interfaz)](../../winscript/reference/idebugstackframesnifferex-interface.md)