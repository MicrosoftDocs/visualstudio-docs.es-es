---
title: IDebugProgram2::GetProgramId | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5edb63de3881d582200199eb8770bde24549b04d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123008"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Obtiene un GUID para este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidProgramId`  
 [out] Devuelve el `GUID` para este programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un motor de depuración (Alemania) debe devolver el identificador de programa que se pasó originalmente para la [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) o [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos. Esto permite identificación del programa en el depurador de componentes.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)