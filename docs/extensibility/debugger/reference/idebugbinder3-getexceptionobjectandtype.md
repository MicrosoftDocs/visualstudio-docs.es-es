---
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee86b12b16cc76b8e2c06ede5ec0110322b515ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891233"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Este método recupera la excepción asociada a un objeto, si existe.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parámetros
`ppException`\
enuncia Devuelve el objeto que representa la excepción.

`ppField`\
enuncia Devuelve el objeto que representa un campo concreto que puede haber provocado la excepción (puede ser un valor null).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

> [!NOTE]
> Para comprobar si hay una excepción, compruebe el valor devuelto por `ppException` : si es un valor null, no habrá ninguna excepción asociada a este objeto.

## <a name="see-also"></a>Vea también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
