---
title: IDebugProperty3::DestroyObjectID ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721199"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Destruye el identificador único asociado a esta propiedad, lo que indica que al autor de la llamada ya no le importa identificar esta propiedad de forma única desde todas las demás propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si el motor de depuración no necesita admitir identificadores únicos para una propiedad (porque `E_NOTIMPL` ya los realiza un seguimiento de forma única internamente), simplemente puede volver para este método.

 Los identificadores únicos se crean con una llamada al método [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) cuando el autor de la llamada desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades.

## <a name="see-also"></a>Vea también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
