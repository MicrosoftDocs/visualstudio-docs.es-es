---
title: IEnumDebugStackFrames::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 486700c387fea139ab4c354dee580652717ff08e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096998"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
Restablece una secuencia de enumeración al principio.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método restablece una secuencia de enumeración al principio.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugStackFrames (Interfaz)](../../winscript/reference/ienumdebugstackframes-interface.md)