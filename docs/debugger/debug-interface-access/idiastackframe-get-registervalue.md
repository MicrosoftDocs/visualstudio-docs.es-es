---
title: Idiastackframe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0bb8f3a10bebbdaff489b2b628af2e1228fdf40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985805"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Recupera el valor de un registro especificado tal como está almacenado en el marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `registerIndex`  
 [in] Uno de los [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md) valores de enumeración.  
  
 `pRetVal`  
 [out] Valor almacenado en el registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)