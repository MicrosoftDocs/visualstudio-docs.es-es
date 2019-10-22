---
title: 'IJsDebugFrame:: GetStackRange ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574041"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange (Método)
Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStart`  
 enuncia Puntero de pila inferior del marco.  
  
 `pEnd`  
 enuncia Puntero de apilador más alto del marco.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Este método es útil para juntar juntos los seguimientos de la pila intercalados recopilados de varios tiempos de ejecución. Los punteros de pila de inicio y fin pueden abarcar varios marcos de pila de máquinas físicas (para los marcos en tiempo de ejecución de JavaScript interpretados). Empiece > end a medida que la pila crezca de la dirección alta a la baja.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)