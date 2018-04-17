---
title: IDebugProcess3::GetENCAvailableState | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a34d9a6f403345bb84f172c416dda62f0109ec2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Este método obtiene el estado actual de editar y continuar del proceso. Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pReason`  
 [out] Un valor de la [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
> [!NOTE]
>  Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
 Este estado puede verse afectado por [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)