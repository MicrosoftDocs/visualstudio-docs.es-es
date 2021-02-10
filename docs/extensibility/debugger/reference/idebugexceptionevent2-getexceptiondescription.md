---
title: 'IDebugExceptionEvent2:: GetExceptionDescription | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4454d9c77cad2050c260d0fbd86764b6bf703403
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933274"
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

## <a name="remarks"></a>Notas
 La cadena devuelta por este método suele ser el nombre de la excepción y se muestra en la ventana de **salida** cuando se produce la excepción.

## <a name="see-also"></a>Vea también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
