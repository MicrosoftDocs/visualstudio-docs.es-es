---
title: "Ijsdebugdatatarget:: Readbstr (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85fbdb556b59c67610ad65b7e1f056399ad6da58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR (Método)
Lee una cadena BSTR desde el destino de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] La dirección que leer.  
  
 `pString`  
 [out] El BSTR lee desde el destino de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_INVALID_MEMORY_ADDRESS si la dirección no es válida.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)