---
title: 'IDebugProgram2:: GetProgramId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7723333547e0aeac7fe7a73c0dc40b36f4b6e071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890037"
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

## <a name="parameters"></a>Parámetros
`pguidProgramId`\
enuncia Devuelve el `GUID` para este programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Un motor DE depuración (DE) debe devolver el [identificador del programa](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) que se pasó originalmente a los métodos Attach o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . Esto permite identificar el programa en todos los componentes del depurador.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
