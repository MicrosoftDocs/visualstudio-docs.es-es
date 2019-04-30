---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3dfec12193efda49a520a40418b93f2d4cef6b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870198"
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Un motor de depuración (DE) debe devolver el identificador de programa que se pasaron originalmente para el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) o [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos. Permite la identificación del programa en el depurador los componentes.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)