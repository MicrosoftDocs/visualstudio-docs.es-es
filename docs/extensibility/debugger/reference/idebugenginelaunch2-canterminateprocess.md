---
title: IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d75fe5b61455029a0c22b5f2deac6ed1d93ee2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964275"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Determina si se puede finalizar un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso que se finalice.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `S_FALSE` si el motor no puede terminar el proceso, por ejemplo, porque se denegó el acceso.  
  
## <a name="remarks"></a>Comentarios  
 Si este método devuelve `S_OK`, a continuación, se la [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) método puede llamarse para realmente finalizan el proceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)