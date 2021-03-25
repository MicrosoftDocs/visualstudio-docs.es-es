---
description: Obtiene una descripción de la excepción que se pueda mostrar.
title: 'IDebugExceptionEvent2:: GetExceptionDescription | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4dc62be4dd7ec4a1db00d8a11dff73b671f8112
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084797"
---
# <a name="idebugexceptionevent2getexceptiondescription"></a>IDebugExceptionEvent2::GetExceptionDescription
Obtiene una descripción de la excepción que se pueda mostrar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetExceptionDescription( 
   BSTR* pbstrDescription
);
```

```csharp
int GetExceptionDescription( 
   out string pbstrDescription
);
```

## <a name="parameters"></a>Parámetros
`pbstrDescription`\
enuncia Devuelve una descripción de la excepción que se pueda mostrar.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La cadena devuelta por este método suele ser el nombre de la excepción y se muestra en la ventana de **salida** cuando se produce la excepción.

## <a name="see-also"></a>Consulte también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
