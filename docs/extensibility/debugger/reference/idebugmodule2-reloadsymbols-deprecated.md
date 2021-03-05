---
description: OBSOLETO. Vuelve a cargar los símbolos para este módulo.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d07f80a3dccef666c0608d79505816f73ff52013
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150528"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NO USE. Vuelve a cargar los símbolos para este módulo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parámetros
`pszUrlToSymbols`\
de La ruta de acceso al almacén de símbolos.

`pbstrDebugMessage`\
enuncia Devuelve un mensaje informativo, como un estado o un mensaje de error, que se muestra a la derecha del nombre del módulo en la ventana módulos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un motor de depuración siempre debe devolver `E_FAIL` .

## <a name="remarks"></a>Observaciones
 Este método ya no se admite. En su lugar, implemente el método [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) .

## <a name="see-also"></a>Consulte también
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
