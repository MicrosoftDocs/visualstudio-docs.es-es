---
title: IEnumDebugStackFrames::Next | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e148b5e13bc3d7986451ece11a3a2eada5baa28
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de segmentos para recuperar.  
  
 `prgdsfd`  
 [out] Devuelve una matriz de `DebugStackFrameDescriptor` interfaces que representa los segmentos que se va a recuperar.  
  
 `pceltFetched`  
 [out] El número real de segmentos capturados por el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugStackFrames (interfaz)](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor (Estructura)](../../winscript/reference/debugstackframedescriptor-structure.md)