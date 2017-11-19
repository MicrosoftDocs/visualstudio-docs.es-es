---
title: "Ijsdebugdatatarget:: Createstackframeenumerator (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation: jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91c67dc3eb14217ffcdc41f0877df6837fcb0230
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>IJsDebugDataTarget::CreateStackFrameEnumerator (Método)
Crea un enumerador para los marcos de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 [in] Subproceso que se ejecuta en el proceso de destino.  
  
 `ppEnumerator`  
 [out] El enumerador de los marcos de pila.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)