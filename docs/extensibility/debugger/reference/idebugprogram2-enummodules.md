---
description: Recupera una lista de los módulos que este programa ha cargado y se está ejecutando.
title: 'IDebugProgram2:: EnumModules (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26016510856de44c07ca9a123553e82d0d2a79f4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149631"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Recupera una lista de los módulos que este programa ha cargado y se está ejecutando.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) que contiene una lista de los módulos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un módulo es un archivo DLL o un ensamblado y, por lo general, se muestra en la ventana de depuración de **módulos** .

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
