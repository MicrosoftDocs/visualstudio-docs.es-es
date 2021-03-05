---
description: Devuelve el número de bytes contenidos en este objeto.
title: 'IEEDataStorage:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46051ae73859213b3206e27fb83d40c0561d0c0b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222931"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Devuelve el número de bytes contenidos en este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parámetros
`size`\
enuncia Número de bytes contenidos en este objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Utilice el método [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) para recuperar los bytes de datos reales.

## <a name="see-also"></a>Consulte también
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
