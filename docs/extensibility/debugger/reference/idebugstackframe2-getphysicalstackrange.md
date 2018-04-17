---
title: IDebugStackFrame2::GetPhysicalStackRange | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be53b50bc21d81c60f7131e8ed437ecb2ac2f16c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtiene una representación dependientes del equipo del intervalo de direcciones físicas asociado a un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `paddrMin`  
 [out] Devuelve la dirección física más bajo asociada con este marco de pila.  
  
 `paddrMax`  
 [out] Devuelve la dirección física mayor asociada con este marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La información devuelta por este método es usar el Administrador de sesión de depuración (SDM) para ordenar los marcos de pila.  
  
 Se supone que la pila de llamadas crece hacia abajo, es decir, que se agregan nuevos marcos de pila en direcciones de memoria cada vez más inferiores. Una arquitectura en tiempo de ejecución debe proporcionar el intervalo de pila física que coincida con esta suposición.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)