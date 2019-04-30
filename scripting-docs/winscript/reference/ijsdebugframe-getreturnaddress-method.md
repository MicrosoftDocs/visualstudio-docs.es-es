---
title: Getreturnaddress (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetReturnAddress
apilocation:
- jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18b98c7a5f92f3745baea5d4f82ae90da0989135
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558168"
---
# <a name="ijsdebugframegetreturnaddress-method"></a>IJsDebugFrame::GetReturnAddress (Método)
Obtiene la dirección de devolución insertada en el 'inicio' (vea GetStackRange) del marco.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pReturnAddress`  
 [out] La dirección de retorno.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)