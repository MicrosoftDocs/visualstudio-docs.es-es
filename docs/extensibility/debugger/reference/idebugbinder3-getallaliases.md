---
description: Este método recupera una lista de alias del programa.
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04e4f9887ff8cfa68ad4fd4b09d160e3ec2d1eaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085174"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Este método recupera una lista de alias del programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parámetros
`uRequest`\
de Número máximo de alias que se van a devolver (especifica la longitud de la matriz pasada a `ppAliases` ).

`ppAliases`\
[in, out] Matriz para rellenar los alias (si se trata de un valor NULL y `uRequest` es 0, devolverá el recuento de alias que se pueden devolver `puFetched` ).

`puFetched`\
enuncia Devuelve el número de alias obtenidos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
