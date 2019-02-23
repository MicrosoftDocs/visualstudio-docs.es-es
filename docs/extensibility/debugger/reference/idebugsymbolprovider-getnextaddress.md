---
title: IDebugSymbolProvider::GetNextAddress | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 574111db390388ee1d0c572a3a8825c3a2ae9469
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722764"
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

#### <a name="parameters"></a>Parámetros
 `pAddress`

 [in] Dada la dirección de depuración.

 `fStatementOnly`

 [in] Si es TRUE, limita las direcciones de depuración para una sola instrucción.

 `ppAddress`

 [out] Devuelve la siguiente dirección de depuración.

## <a name="return-value"></a>Valor devuelto
 Devuelve un válidas `HRESULT`, normalmente S_OK.

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)