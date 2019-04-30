---
title: IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec878a08e6f22a461eee95f31db7fa2a1bc97886
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431568"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
Determina si la suma de comprobación está habilitada para este documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsChecksumEnabled(
   BOOL *pfChecksumEnabled
);
```

```csharp
public int IsChecksumEnabled(
   out int pfChecksumEnabled
);
```

#### <a name="parameters"></a>Parámetros
 `pfChecksumEnabled`

 [out] Devuelve TRUE si la suma de comprobación está habilitada; en caso contrario, devuelve FALSE.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)