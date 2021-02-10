---
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
ms.openlocfilehash: 6afc0f5243d9f50f2d777c0bd43e6bba1de5e495
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936111"
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

## <a name="remarks"></a>Notas
 Si el motor de depuración no necesita admitir identificadores únicos para una propiedad (porque ya realiza un seguimiento de ellos de forma exclusiva), puede devolver simplemente `E_NOTIMPL` para este método.

 Los identificadores únicos se crean con una llamada al método [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) cuando el llamador desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades.

## <a name="see-also"></a>Vea también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
