---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9abab3122921619ba14400bb14039fac139a159f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933807"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Adjunta el programa asociado o se aplaza el proceso de conexión para el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidProgramId`  
 [in] `GUID` para asignar al programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) no se debe llamar al método. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama durante el proceso de asociación, antes del [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) se llama al método. El `OnAttach` método puede realizar el proceso de conexión propia (en este caso, se devuelve este método `S_FALSE`) o aplazar el proceso de conexión para el `IDebugEngine2::Attach` método (el `OnAttach` devuelve del método `S_OK`). En cualquier caso, el `OnAttach` método puede establecer el `GUID` del programa que se está depurando el determinado `GUID`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)