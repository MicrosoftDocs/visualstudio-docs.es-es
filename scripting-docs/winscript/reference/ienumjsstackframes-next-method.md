---
title: 'Ienumjsstackframes:: Next (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2068bd130e7eb03747b89e2ba107019aa1cd458
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727715"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next (Método)
Obtiene el número especificado de fotogramas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cFrameCount`  
 [in] El número de fotogramas que desea obtener.  
  
 `pFrames`  
 [out] La matriz para almacenar los fotogramas.  
  
 `pcFetched`  
 [out] Devuelve el número de fotogramas.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IEnumJsStackFrames (Interfaz)](../../winscript/reference/ienumjsstackframes-interface.md)