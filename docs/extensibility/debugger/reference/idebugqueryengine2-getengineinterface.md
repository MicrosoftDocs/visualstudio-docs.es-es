---
title: 'IDebugQueryEngine2:: GetEngineInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab1d9be5e4405cea3bb75d7837d4ff3ad9a91e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909788"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Obtiene una interfaz personalizada del motor DE depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parámetros
`ppUnk`\
enuncia Devuelve un `IUnknown` objeto que representa el motor de depuración (de) y que se puede consultar para cualquier otra interfaz válida asociada a un de (por ejemplo, [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La interfaz resultante debe usarse con cuidado, ya que la llamada a través de las interfaces recuperadas de este método evita el procesamiento del administrador de depuración de la sesión y puede dar lugar a un estado incorrecto o a generar errores durante la depuración.

## <a name="see-also"></a>Vea también
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
