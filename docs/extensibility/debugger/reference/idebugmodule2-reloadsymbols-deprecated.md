---
title: IDebugModule2::ReloadSymbols_Deprecated Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726920"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NO USAR. Vuelve a cargar los símbolos de este módulo.

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
[en] La ruta de acceso al almacén de símbolos.

`pbstrDebugMessage`\
[fuera] Devuelve un mensaje informativo, como un estado o un mensaje de error, que se muestra a la derecha del nombre del módulo en la ventana Módulos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un motor de `E_FAIL`depuración siempre debe devolver .

## <a name="remarks"></a>Observaciones
 Este método ya no es compatible. Implemente el método [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) en su lugar.

## <a name="see-also"></a>Vea también
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
