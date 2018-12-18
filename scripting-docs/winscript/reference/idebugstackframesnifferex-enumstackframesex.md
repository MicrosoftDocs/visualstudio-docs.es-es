---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Documentos de Microsoft
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
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727585"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Devuelve un enumerador de los marcos de pila del subproceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSpMin`  
 [in] El límite inferior de dirección para enumerar los marcos de pila.  
  
 `ppedsf`  
 [out] Enumerador de los marcos de pila del subproceso actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El enumerador de marco de pila devuelve los fotogramas desde la parte superior de la pila, con el marco insertado más recientemente. El enumerador contiene marcos de pila solo con direcciones mayores o iguales que `dwSpMin`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrameSnifferEx (Interfaz)](../../winscript/reference/idebugstackframesnifferex-interface.md)