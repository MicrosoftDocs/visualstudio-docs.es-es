---
title: IDebugProperty3::CreateObjectID ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721179"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es única entre todas las demás propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método cuando el administrador de depuración de sesión desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades. El motor de depuración (DE) admite este método a menos que las propiedades con las que trata ya se identifican de forma única. Si el DE no admite este `E_NOTIMPL`método, devuelve .

 Cualquier identificador único `CreateObjectID` creado con se destruye cuando el [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) se llama al método; esto también indica el fin de la necesidad de identificar de forma única esta propiedad.

> [!NOTE]
> No hay ningún método para recuperar este identificador único, por lo que `CreateObjectID` la DE puede hacer lo que quiera para identificadores únicos cuando se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
