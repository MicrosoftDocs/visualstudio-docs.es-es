---
title: Método Ijsdebugdatatarget | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154691"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext (Método)
Recupera contexto para el subproceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 [in] Subproceso que se ejecuta en el proceso de destino.  
  
 `contextFlags`  
 [in] Especifica las marcas de contexto. Es el mismo que el campo ContextFlags de CONTEXT (para obtener más información, vea winnt.h y busque CONTEXT_ALL).  
  
 `contextSize`  
 [in] El tamaño del búfer especificado por pContext.  
  
 `pContext`  
 [out] Recibe la estructura CONTEXT específica de plataforma en el búfer especificado por pContext.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)