---
title: IDebugMemoryBytes2::GetSize | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fce2d9beecb6c2a51d64e229dcf386795ab55f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Recupera el tamaño, en bytes, de la memoria representado por este [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pqwSize`  
 [out] Devuelve el tamaño, en bytes del espacio de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)