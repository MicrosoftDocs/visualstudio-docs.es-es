---
title: IPropertyProxyEESide::CreateReplacementObject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715034"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia de un objeto de datos específico del evaluador de expresiones (EE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parámetros
`dataIn`\
[en] Objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los datos que se van a copiar.

`dataOut`\
[out] Devuelve un nuevo objeto `IEEDataStorage`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 A este método se le proporciona un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que representa una matriz de bytes. Este objeto de datos entrante normalmente no se implementa por el EE. Sin embargo, el objeto devuelto por este método siempre es implementado `IEEDataStorage` por el EE, que permite a EE implementar la interfaz en cualquier clase que se desee.

 Tenga en cuenta que `IEEDataStorage` los datos proporcionados por `IEEDataStorage` el objeto entrante deben ser los mismos datos en el objeto saliente.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
