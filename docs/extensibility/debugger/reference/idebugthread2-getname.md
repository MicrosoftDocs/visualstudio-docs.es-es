---
description: Obtiene el nombre de un subproceso.
title: 'IDebugThread2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d3be2cf827929f41532cf7f1dbf6b709c1850dc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164609"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtiene el nombre de un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pbstrName`\
enuncia Devuelve el nombre del subproceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El nombre recuperado es siempre un nombre que se puede mostrar y este nombre describe el subproceso. El nombre del subproceso podría derivarse de una arquitectura en tiempo de ejecución que admita subprocesos con nombre, o podría ser un nombre derivado del motor de depuración. Como alternativa, el nombre del subproceso se puede establecer mediante una llamada al método [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
