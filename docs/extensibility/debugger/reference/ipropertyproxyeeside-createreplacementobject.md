---
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30e2b8037059824bd514024e6fb86561406895c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852835"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia de un objeto de datos específico del evaluador de expresiones (EE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parámetros
`dataIn`\
de Un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los datos que se van a copiar.

`dataOut`\
[out] Devuelve un nuevo objeto `IEEDataStorage`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 A este método se le asigna un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que representa una matriz de bytes. Este objeto de datos de entrada no suele ser implementado por EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante el, que permite a EE implementar la `IEEDataStorage` interfaz en cualquier clase deseada.

 Tenga en cuenta que los datos proporcionados por el objeto de entrada `IEEDataStorage` deben ser los mismos en el objeto de salida `IEEDataStorage` .

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
