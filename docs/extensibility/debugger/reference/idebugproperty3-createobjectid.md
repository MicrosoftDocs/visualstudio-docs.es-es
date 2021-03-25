---
description: Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af90f360e59e04cc5d55017c5d986e6682bab2ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064818"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método cuando el administrador de depuración de la sesión desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades. El motor DE depuración (DE) admite este método a menos que las propiedades a las que se ocupan ya se identifiquen de forma única. Si DE no admite este método, devuelve `E_NOTIMPL` .

 Los IDENTIFICADOres únicos creados con `CreateObjectID` se destruyen cuando se llama al método [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; esto también indica el final de la necesidad de identificar de forma única esta propiedad.

> [!NOTE]
> No hay ningún método para recuperar este identificador único, por lo que el DE puede hacer todo lo que desee para los identificadores únicos cuando `CreateObjectID` se llama al método.

## <a name="see-also"></a>Consulte también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
