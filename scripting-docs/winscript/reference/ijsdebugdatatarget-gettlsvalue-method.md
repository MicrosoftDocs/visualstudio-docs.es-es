---
title: 'IJsDebugDataTarget:: Gettlsvalue ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577604"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue (Método)
Para el subproceso que se está depurando, recupera el valor de la ranura de almacenamiento local para el subproceso (TLS) para el índice TLS especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 de Subproceso que se ejecuta en el proceso de destino desde el que se va a leer.  
  
 `tlsIndex`  
 de Índice de TLS que se asignó cuando el proceso de destino llamó a la función TlsAlloc.  
  
 `pValue`  
 enuncia Valor del tamaño del puntero que se almacenó en la ranura TLS del subproceso. Si el subproceso de destino es de 32 bits, los 32 bits superiores de este valor serán cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Cada subproceso de un proceso tiene su propia ranura para cada índice de TLS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)