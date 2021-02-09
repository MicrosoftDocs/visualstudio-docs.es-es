---
title: 'IDebugField:: GetTypeInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f74cc24d7698c3d83991c7f338bd2ef155ee1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869796"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Este método obtiene información independiente del tipo sobre el símbolo o tipo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parámetros
`pTypeInfo`\
enuncia Devuelve información de tipo en la estructura de [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) proporcionada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La información independiente del tipo incluiría, por ejemplo, el AppDomain, el módulo y la clase que contiene el símbolo.

## <a name="see-also"></a>Vea también
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
