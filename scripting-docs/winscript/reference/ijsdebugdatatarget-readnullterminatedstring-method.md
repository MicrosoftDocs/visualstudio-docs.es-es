---
title: 'Ijsdebugdatatarget:: Readnullterminatedstring (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729505"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString (Método)
Lee el número especificado de caracteres desde el destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] La dirección que leer.  
  
 `characterSize`  
 [in] tamaño de cada carácter de la cadena  
  
 `maxCharacters`  
 [in] El número máximo de caracteres que se va a leer. maxCharacters debe ser razonable. Se producirá un error en cualquier solicitud de más de 128MB de memoria.  Si la cadena es mayor que maxCharacters, la cadena de resultado se truncará después maxCharacters.  
  
 `pString`  
 [out] El BSTR lee desde el destino.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelva S_FALSE si truncado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)