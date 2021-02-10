---
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
ms.openlocfilehash: b8648890e030799b985a4e917be8caf85292528a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947104"
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

## <a name="remarks"></a>Notas
 Las clases base del objeto de enumerador se especifican en orden de la clase base más inmediata (o más derivada) a la clase base más remota. Por ejemplo, dadas las clases de C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 La enumeración devolvería las clases base en el orden `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
