---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74889ed04dceb133c80467d20f723f9561b6e25c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703830"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crea un enumerador para las clases base de esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parámetros
 `ppEnum`

 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de clases bases. Devuelve un valor null si no hay ninguna clase base.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK, se devuelve S_SH_NO_BASE_CLASSES si no hay ninguna clase base (y el `ppEnum` parámetro se establece en un valor null); en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Las clases base en el objeto de enumerador se especifican en orden de la clase base más inmediata (o más derivada) a la clase base más remota. Por ejemplo, con las clases de C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 La enumeración devolvería las clases base en el orden `Level2`, `Level1`, `Root`.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)