---
description: Establece el servidor principal para el proveedor del puerto.
title: 'IDebugPortSupplierEx2:: SetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81de22828536dd118cb69ed4c3c73d51f55a8535
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071914"
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
Establece el servidor principal para el proveedor del puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetServer(
   IDebugCoreServer2* pServer
);
```

```csharp
int SetServer(
   IDebugCoreServer2 pServer
);
```

## <a name="parameters"></a>Parámetros
`pServer`\
Servidor principal que se va a establecer para el proveedor del puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)
