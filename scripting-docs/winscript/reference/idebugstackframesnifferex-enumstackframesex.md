---
title: 'Idebugstackframesnifferex (:: EnumStackFramesEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576703"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Devuelve un enumerador de marcos de pila para el subproceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSpMin`  
 de Límite de dirección inferior para la enumeración de marcos de pila.  
  
 `ppedsf`  
 enuncia Enumerador de marcos de pila para el subproceso actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El enumerador de marco de pila devuelve los fotogramas que comienzan en la parte superior de la pila, con el marco insertado más recientemente. El enumerador solo contiene marcos de pila con direcciones mayores o iguales que `dwSpMin`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrameSnifferEx (Interfaz)](../../winscript/reference/idebugstackframesnifferex-interface.md)