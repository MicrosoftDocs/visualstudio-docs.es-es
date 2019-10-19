---
title: 'IJsDebugDataTarget:: GetThreadContext (método) | Microsoft Docs'
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
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577658"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext (Método)
Recupera el contexto del subproceso especificado.  
  
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
 de Subproceso que se ejecuta en el proceso de destino.  
  
 `contextFlags`  
 de Especifica las marcas de contexto. Este es el mismo que el campo ContextFlags de context (para obtener más información, vea Winnt. h, busque CONTEXT_ALL).  
  
 `contextSize`  
 de Tamaño del búfer especificado por pContext.  
  
 `pContext`  
 enuncia Recibe la estructura de contexto específica de la plataforma en el búfer especificado por pContext.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)