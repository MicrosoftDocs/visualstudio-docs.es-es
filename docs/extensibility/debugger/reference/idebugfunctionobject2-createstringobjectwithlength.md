---
description: Crea un objeto de cadena que tiene la longitud especificada.
title: 'IDebugFunctionObject2:: CreateStringObjectWithLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 637b9837cdc351e9f717a773302fbfe6f6588f46
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149961"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crea un objeto de cadena que tiene la longitud especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`pcstrString`\
de Valor de cadena para el objeto de cadena.

`uiLength`\
de Longitud de la cadena en bytes.

`ppObject`\
enuncia Devuelve un objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto de cadena que se acaba de crear.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
