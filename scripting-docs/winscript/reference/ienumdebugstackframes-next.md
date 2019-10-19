---
title: 'Ienumdebugstackframes (:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575547"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Recupera un número especificado de segmentos en la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 de Número de segmentos que se van a recuperar.  
  
 `prgdsfd`  
 enuncia Devuelve una matriz de interfaces `DebugStackFrameDescriptor` que representa los segmentos que se van a recuperar.  
  
 `pceltFetched`  
 enuncia Número real de segmentos capturados por el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera un número especificado de segmentos en la secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz ienumdebugstackframes (](../../winscript/reference/ienumdebugstackframes-interface.md)  
 [DebugStackFrameDescriptor (Estructura)](../../winscript/reference/debugstackframedescriptor-structure.md)