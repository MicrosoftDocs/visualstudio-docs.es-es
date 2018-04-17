---
title: IDebugAddress2::GetProcessID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbe84371deb7306300c69f4890398fd43c3061f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera el identificador del proceso que posee el objeto representado por este [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProcID`  
 [out] El identificador del proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)