---
title: "Ijsdebugdatatarget:: GetTLSValue (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue (Método)
Para el subproceso que se está depurando, recupera el valor de la ranura de almacenamiento local (TLS) del subproceso para el índice especificado de TLS.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 [in] Subproceso que se ejecuta en el proceso de destino para leer desde.  
  
 `tlsIndex`  
 [in] El índice TLS que se asignó cuando el proceso de destino llama a la función TlsAlloc.  
  
 `pValue`  
 [out] El valor de tamaño de puntero que se almacena en la ranura TLS del subproceso. Si el subproceso de destino es de 32 bits, los 32 bits superiores de este valor será cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Cada subproceso de un proceso tiene su propio espacio para cada índice TLS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)