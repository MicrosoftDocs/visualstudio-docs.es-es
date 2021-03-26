---
description: Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los datos nuevos del objeto.
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fb6c098d26148db39493b25f199c6819fb81d27
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082418"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los datos nuevos del objeto.

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
de Un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los nuevos datos.

`dataOut`\
enuncia Devuelve un nuevo `IEEDataStorage` objeto que contiene los datos reemplazados.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En realidad, este método actualiza los datos del objeto. No es necesario que los datos del objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) devuelto sean los mismos que los datos del objeto entrante `IEEDataStorage` , pero el objeto devuelto debe reflejar el valor actual de la propiedad.

 El objeto de datos de entrada no suele ser implementado por EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante el, que permite a EE implementar la `IEEDataStorage` interfaz en cualquier clase deseada.

 El método [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un objeto de datos basado en el objeto de datos de entrada, pero no afecta a los datos originales de la propiedad.

## <a name="see-also"></a>Consulte también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
