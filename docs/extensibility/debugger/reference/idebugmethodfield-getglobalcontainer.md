---
title: 'IDebugMethodField:: GetGlobalContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 197490cde12e0c7dd9cee14d11c3ec2f0b165d86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936878"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Obtiene el contenedor global del método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parámetros
`ppClass`\
enuncia Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el módulo en el que se define este método.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 El objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) devuelto representa todo el módulo y es un objeto artificial, es decir, el propio módulo no tiene una clase real, pero se puede representar mediante un `IDebugClassField` objeto, lo que permite enumerar y detectar los distintos elementos del módulo.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
