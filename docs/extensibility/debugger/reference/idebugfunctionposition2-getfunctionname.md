---
title: 'IDebugFunctionPosition2:: GetFunctionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d26574dd05f5f7dcdb7414df1ffb71f2ef2e4cd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921023"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Obtiene el nombre de la función a la que señala esta posición.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetFunctionName( 
   BSTR* pbstrFunctionName
);
```

```csharp
int GetFunctionName(
   out string pbstrFunctionName
);
```

## <a name="parameters"></a>Parámetros
`pbstrFunctionName`\
enuncia Devuelve el nombre de la función.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
