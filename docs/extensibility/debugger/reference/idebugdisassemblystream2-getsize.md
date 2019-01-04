---
title: IDebugDisassemblyStream2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ccdb3a4e02403ec10da814770816ce78feb65f6d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887258"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtiene el tamaño en las instrucciones de esta secuencia de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pnSize`  
 [out] Devuelve el tamaño, en las instrucciones.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto de este método puede utilizarse para asignar una matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructuras que, a continuación, se pasa a la [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)