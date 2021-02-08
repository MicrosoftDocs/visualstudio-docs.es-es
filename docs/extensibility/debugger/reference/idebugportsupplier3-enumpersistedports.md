---
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09b1fabaeb5bf887eedaa53d57bdeb3604bf2257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840332"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Este método recupera un objeto que permite la enumeración de la lista de puertos persistentes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`PortNames`\
de [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) estructura que contiene la lista de nombres de puerto que se van a buscar y devolver entre los puertos persistentes. Solo se devolverán los puertos persistentes con estos nombres.

`ppEnum`\
enuncia Objeto que implementa la interfaz [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Los puertos persistentes se cargan cuando se crea una instancia de un proveedor de puerto y se guardan cuando se destruye el proveedor del puerto.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
