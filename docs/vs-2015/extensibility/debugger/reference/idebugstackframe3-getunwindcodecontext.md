---
title: IDebugStackFrame3::GetUnwindCodeContext | Documentos de Microsoft
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
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f450454b7eba05e0267a9fb5a4ed10c8940e153
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574035"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugStackFrame3::GetUnwindCodeContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext).  
  
Devuelve el contexto del código que representa una ubicación si la operación de desenredo de pila se ha producido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppCodeContext`  
 [out] Devuelve un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa la ubicación del contexto de código si se ha producido un desenredo de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Aunque este método puede devolver un contexto de código para la ubicación después de un desenredo de pila, eso no significa necesariamente que realmente puede producirse el desenredo de pila en el marco de pila actual.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

