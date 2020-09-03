---
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721179"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.

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
 Se llama a este método cuando el administrador de depuración de la sesión desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades. El motor DE depuración (DE) admite este método a menos que las propiedades a las que se ocupan ya se identifiquen de forma única. Si DE no admite este método, devuelve `E_NOTIMPL` .

 Los IDENTIFICADOres únicos creados con `CreateObjectID` se destruyen cuando se llama al método [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; esto también indica el final de la necesidad de identificar de forma única esta propiedad.

> [!NOTE]
> No hay ningún método para recuperar este identificador único, por lo que el DE puede hacer todo lo que desee para los identificadores únicos cuando `CreateObjectID` se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
