---
title: IDebugThread2::GetThreadId | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c73993c9e596f8d7798dd6f5b92c3478e1d5dda
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577628"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugThread2::GetThreadId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-getthreadid).  
  
Obtiene el identificador de subproceso del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```csharp  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwThreadId`  
 [out] Devuelve el identificador de subproceso del sistema.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un identificador de subproceso se usa para identificar un subproceso entre todos los demás subprocesos en un proceso.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto que implementa el [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaz.  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

