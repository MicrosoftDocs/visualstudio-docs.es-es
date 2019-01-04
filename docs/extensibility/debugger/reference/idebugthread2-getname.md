---
title: IDebugThread2::GetName | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d53d0e9a76caa1341494cea93311f9c912191c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948685"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtiene el nombre de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 [out] Devuelve el nombre del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El nombre recuperado siempre es un nombre que se puede mostrar y este nombre describe el subproceso. El nombre del subproceso puede derivarse de una arquitectura de tiempo de ejecución que admite denominado subprocesos, o podría ser un nombre derivado el motor de depuración. Como alternativa, se puede establecer el nombre del subproceso mediante una llamada a la [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)