---
title: IJsDebugProcess::P método erformAsyncBreak | Microsoft Docs
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
ms.openlocfilehash: 3320c59097dec5229030a3f15252d907562c67e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577329"
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
 de IDENTIFICADOR del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProcess (Interfaz)](../../winscript/reference/ijsdebugprocess-interface.md)