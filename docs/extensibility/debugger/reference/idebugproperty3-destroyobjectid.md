---
description: Destruye el identificador único asociado a esta propiedad, que indica que el autor de la llamada ya no le importa que identifique esta propiedad de forma única desde todas las demás propiedades.
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3712a12440f5d177f54544110bc8fa5d2e03ac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166702"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Destruye el identificador único asociado a esta propiedad, que indica que el autor de la llamada ya no le importa que identifique esta propiedad de forma única desde todas las demás propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si el motor de depuración no necesita admitir identificadores únicos para una propiedad (porque ya realiza un seguimiento de ellos de forma exclusiva), puede devolver simplemente `E_NOTIMPL` para este método.

 Los identificadores únicos se crean con una llamada al método [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) cuando el llamador desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades.

## <a name="see-also"></a>Consulte también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
