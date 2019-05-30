---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50fb7800c4446e7d13334957ee9f5f6534f254bf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338224"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera una interfaz de código administrado que representa el valor asociado a este alias.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parámetros
`ppUnk`\
[out] `IUnknown` interfaz que representa el valor asociado a este alias. Esta interfaz se puede consultar el `ICorDebugValue` interfaz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método solo se aplica a valores administrados (el `ICorDebugValue` está disponible en una interfaz el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] y se define en el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK en el archivo cordebug.idl).

## <a name="see-also"></a>Vea también
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)