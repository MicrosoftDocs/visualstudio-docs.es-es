---
title: IDebugProgramNodeAttach2::OnAttach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords: IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c5a70baa682af956e6337c89b2c01b3f9c29ebd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Se une al programa o pasa el proceso de conexión para el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
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
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método no debe llamarse. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama durante el proceso de conexión, antes del [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) se llama al método. El `OnAttach` método puede realizar el proceso de conexión propia (en este caso, este método devuelve `S_FALSE`) o aplazar el proceso de conexión para el `IDebugEngine2::Attach` método (el `OnAttach` método devuelve `S_OK`). En cualquier caso, el `OnAttach` método puede definir la `GUID` del programa que se está depurando el determinado `GUID`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)