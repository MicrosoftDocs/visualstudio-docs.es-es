---
title: IDebugModOpt::GetModOpts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4cd6042219e03d9e3ca3b6192b49ccfda6881416
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689699"
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

#### <a name="parameters"></a>Parámetros
 `celt`

 [in] Número de elementos que se va a devolver.

 `rgelt`

 [out] Devuelve una matriz que contiene las opciones.

 `pceltFetched`

 [in, out] Número de elementos devueltos en la `rgelt` matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)