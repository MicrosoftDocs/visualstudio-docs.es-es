---
title: IDebugThreadDestroyEvent2::GetExitCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56caa01fa99e515437116d4d6af9e9be696ac334
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977699"
---
# <a name="idebugthreaddestroyevent2getexitcode"></a>IDebugThreadDestroyEvent2::GetExitCode
Obtiene el código de salida para un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetExitCode (   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode (   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwExit`  
 [out] Devuelve el código de salida del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)