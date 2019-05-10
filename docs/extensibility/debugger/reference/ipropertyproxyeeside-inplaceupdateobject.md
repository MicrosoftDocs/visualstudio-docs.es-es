---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a233a37f83ff3f75b5cf0ec103e59da91f1473bd
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458458"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los datos del objeto nuevo.

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

 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contiene los nuevos datos.

 `dataOut`\

 [out] Devuelve un nuevo `IEEDataStorage` objeto que contiene los datos reemplazados.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método realmente actualiza los datos del objeto. Los datos en el valor devuelto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto no necesita ser el mismo que los datos de entrada `IEEDataStorage` objeto, pero el objeto devuelto debe reflejar el valor actual de la propiedad.

 El objeto de datos entrantes no se suele implementar mediante lo EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante EE, lo que permite la implemente EE el `IEEDataStorage` interfaz en cualquier clase es el deseado.

 El [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método crea un objeto de datos basado en el objeto de datos entrantes, pero no afecta a los datos originales de la propiedad.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)