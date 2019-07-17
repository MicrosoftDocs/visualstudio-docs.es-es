---
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a98840982d44c2ee2348ca5c321d08cc6c46ffc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196244"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve un objeto de contexto de código correspondiente a un identificador de ubicación de código especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `uCodeLocationId`  
 [in] Especifica el identificador de ubicación del código. Consulte la sección Comentarios para el [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método para obtener una descripción de un identificador de ubicación del código.  
  
 `ppCodeContext`  
 [out] Devuelve un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto de código asociado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El identificador de ubicación de código se puede devolver desde una llamada a la [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) método y puede aparecer en el [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura.  
  
 Para convertir un contexto de código en un identificador de ubicación del código, llame a la [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
