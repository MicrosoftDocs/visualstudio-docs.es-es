---
description: Recupera información sobre el método en la dirección de depuración especificada.
title: 'IDebugSymbolProviderDirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306cb3bbe863ed0d8ca37c50b44158ea087ac015
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071095"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Recupera información sobre el método en la dirección de depuración especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
de Dirección de depuración representada por la interfaz [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pGuid`\
enuncia Identificador único del módulo.

`pAppID`\
enuncia Identificador del dominio de aplicación.

`pTokenClass`\
enuncia Token que representa la clase contenedora.

`pTokenMethod`\
enuncia Token que representa el módulo.

`pdwOffset`\
enuncia Desplazamiento en bytes desde el inicio del `pAddress` parámetro.

`pdwVersion`\
enuncia Número de versión del método.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
