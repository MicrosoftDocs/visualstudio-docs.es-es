---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9068eed8881124e75f06f4b97d3430ff3ef80e8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918685"
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

## <a name="remarks"></a>Comentarios
 Este método carga los símbolos desde la ruta de acceso de búsqueda actual (que se puede modificar mediante una llamada a la [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) método).

 Este método es preferible el [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) método.

## <a name="see-also"></a>Vea también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)