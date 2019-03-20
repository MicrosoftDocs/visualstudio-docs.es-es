---
title: Método Ijsdebugprocess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a4fdb70341744c764779d406372bbd55418fd29
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150730"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>IJsDebugProcess::PerformAsyncBreak (Método)
Pone el motor de scripts en modo de interrupción, haciendo que se detenga en la siguiente instrucción de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadId`  
 [in] El identificador de subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProcess (Interfaz)](../../winscript/reference/ijsdebugprocess-interface.md)