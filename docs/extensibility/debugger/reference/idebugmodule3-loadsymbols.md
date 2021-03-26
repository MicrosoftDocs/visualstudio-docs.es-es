---
description: Carga los símbolos del módulo actual.
title: 'IDebugModule3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e8a9c34c85263ab538bf07b10b87f12fddf12db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065520"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carga los símbolos del módulo actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Valor devuelto
 Si el método se realiza correctamente, devuelve `S_OK`. Si se produce un error, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método carga los símbolos de la ruta de acceso de búsqueda actual (que se puede modificar llamando al método [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).

 Este método es preferible que el método [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .

## <a name="see-also"></a>Consulte también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
