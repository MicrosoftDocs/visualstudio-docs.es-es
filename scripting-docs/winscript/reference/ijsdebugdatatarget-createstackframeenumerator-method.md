---
title: Createstackframeenumerator (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 399d66b9f21146f66df86bad0c151722f2893fc8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097752"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>IJsDebugDataTarget::CreateStackFrameEnumerator (Método)
Crea un enumerador para marcos de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 [in] Subproceso que se ejecuta en el proceso de destino.  
  
 `ppEnumerator`  
 [out] El enumerador para marcos de pila.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)