---
title: IPropertyProxyEEside::InPlaceUpdateObject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714893"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los nuevos datos del objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parámetros
`dataIn`\
[en] Un [objeto IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los nuevos datos.

`dataOut`\
[fuera] Devuelve un `IEEDataStorage` nuevo objeto que contiene los datos reemplazados.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método actualiza realmente los datos del objeto. Los datos del objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) devuelto no necesitan ser los `IEEDataStorage` mismos que los datos del objeto entrante, pero el objeto devuelto debe reflejar el valor actual de la propiedad.

 El objeto de datos entrante normalmente no se implementa por el EE. Sin embargo, el objeto devuelto por este método siempre es implementado `IEEDataStorage` por el EE, que permite a EE implementar la interfaz en cualquier clase que se desee.

 El [método CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un objeto de datos basado en el objeto de datos entrante, pero no afecta a los datos originales de la propiedad.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
