---
title: 'IJsDebugDataTarget:: Readnullterminatedstring ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572402"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString (Método)
Lee el número especificado de caracteres del destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 de Dirección de la que se va a leer.  
  
 `characterSize`  
 [in] tamaño de cada carácter de la cadena  
  
 `maxCharacters`  
 de Número máximo de caracteres que se van a leer. maxCharacters debe ser razonable. Se producirá un error en cualquier solicitud de más de 128 MB de memoria.  Si la cadena es mayor que maxCharacters, la cadena de resultado se truncará después de maxCharacters.  
  
 `pString`  
 enuncia BSTR leído del destino.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve S_FALSE si se trunca.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)