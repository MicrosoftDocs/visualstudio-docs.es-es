---
description: Crea un enumerador para las clases base de esta clase.
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d5ef86e5f4fea89b376404703000c8bd7e861a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150723"
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

## <a name="parameters"></a>Parámetros
`ppEnum`\

enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de clases base. Devuelve un valor NULL si no hay ninguna clase base.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK, devuelve S_SH_NO_BASE_CLASSES si no hay ninguna clase base (y el `ppEnum` parámetro se establece en un valor null); de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las clases base del objeto de enumerador se especifican en orden de la clase base más inmediata (o más derivada) a la clase base más remota. Por ejemplo, dadas las clases de C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 La enumeración devolvería las clases base en el orden `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Consulte también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
