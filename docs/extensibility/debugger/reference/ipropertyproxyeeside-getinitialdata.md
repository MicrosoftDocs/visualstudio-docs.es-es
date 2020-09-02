---
title: 'IPropertyProxyEESide:: GetInitialData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetInitialData
helpviewer_keywords:
- IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 650e4bc5cb88800ffd7c61693118c3c2081877c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714988"
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
Devuelve los datos iniciales de este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInitialData(
   IEEDataStorage** dataOut
);
```

```csharp
int GetInitialData(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parámetros
`dataOut`\
enuncia Devuelve un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los datos iniciales de este objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
