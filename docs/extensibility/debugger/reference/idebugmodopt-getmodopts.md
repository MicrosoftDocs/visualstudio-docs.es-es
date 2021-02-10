---
title: 'IDebugModOpt:: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78ddcaa6a062b844c3f60c04f7a08aa673c69f67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941793"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Recupera una lista de modificadores opcionales.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celt`\
de Número de elementos que se van a devolver.

`rgelt`\
enuncia Devuelve una matriz que contiene las opciones.

`pceltFetched`\
[in, out] Número de elementos devueltos en la `rgelt` matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
