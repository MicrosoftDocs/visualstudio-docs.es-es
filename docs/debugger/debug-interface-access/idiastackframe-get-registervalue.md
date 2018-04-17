---
title: 'Idiastackframe:: Get_registervalue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: e38d94d5c79438b103b4db9a16164ffe482c356b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Recupera el valor de un registro especificado tal como se almacena en el marco de pila.  
  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md)