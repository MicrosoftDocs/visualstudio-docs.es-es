---
title: 'IDebugPortSupplierLocale2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ba94e40e475527b586c3e9da33bbf1a893295a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840111"
---
# <a name="idebugportsupplierlocale2setlocale"></a>IDebugPortSupplierLocale2::SetLocale
Establece la configuración regional del proveedor del puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parámetros
`wLangID`\
Identificador de la configuración regional que se va a establecer.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)
