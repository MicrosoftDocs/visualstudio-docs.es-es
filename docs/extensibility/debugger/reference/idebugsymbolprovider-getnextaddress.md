---
title: IDebugSymbolProvider::GetNextAddress | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f358abe84987b9c7c1a5a1df36fdf480f62ee64b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347528"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Obtiene la dirección de depuración que sigue a una dirección de depuración especificado en un método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[in] Dada la dirección de depuración.

`fStatementOnly`\
[in] Si es TRUE, limita las direcciones de depuración para una sola instrucción.

`ppAddress`\
[out] Devuelve la siguiente dirección de depuración.

## <a name="return-value"></a>Valor devuelto
 Devuelve un válidas `HRESULT`, normalmente S_OK.

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)