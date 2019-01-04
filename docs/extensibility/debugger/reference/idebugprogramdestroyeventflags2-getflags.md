---
title: IDebugProgramDestroyEventFlags2::GetFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetFlags
- IDebugProgramDestroyEventFlags2::GetFlags
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae4fc422c94c62529632d94ed8fb844938cd6eed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834378"
---
# <a name="idebugprogramdestroyeventflags2getflags"></a>IDebugProgramDestroyEventFlags2::GetFlags
Recupera el programa destruir marcas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetFlags(  
   PROGRAM_DESTROY_FLAGS* pdwFlags  
);  
```  
  
```csharp  
public int GetFlags(  
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwFlags`  
 [out] Representa el programa destruir marcas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)   
 [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)