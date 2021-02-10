---
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0ff27438ad4a7d0106c1b452f55966dda3f7e07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965569"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera el número especificado de bytes del objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parámetros
`dataSize`\
de Número de bytes que se van a recuperar (la `data` matriz debe contener al menos este número de bytes).

`sizeGotten`\
enuncia Devuelve el número de bytes recuperados realmente.

`data`\
[in, out] Matriz que se va a rellenar con los datos solicitados.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 El uso recomendado de este método es recuperar todos los bytes de datos en una matriz local, ya que no hay ninguna manera de omitir los bytes en el proceso de recuperación. En este caso, el parámetro `dataSize` debe ser el valor devuelto por el método se [obtiene](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .

## <a name="see-also"></a>Vea también
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize (](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
