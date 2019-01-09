---
title: IEnumDebugStackFrames::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28821d90bc27d23d51db00e871807a2ccef885b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097518"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Omite un número especificado de segmentos en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de segmentos de la secuencia de enumeración que se omitirán.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método omite un número especificado de segmentos en una secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugStackFrames (Interfaz)](../../winscript/reference/ienumdebugstackframes-interface.md)