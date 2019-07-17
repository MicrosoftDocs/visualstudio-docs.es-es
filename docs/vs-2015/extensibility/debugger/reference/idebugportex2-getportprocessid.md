---
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50041c41874edbbb66d0e19023d32e50686a8bfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188493"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Obtiene el identificador de proceso del puerto de sí mismo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

#### <a name="parameters"></a>Parámetros
 `pdwProcessId`

 [out] Devuelve el identificador de proceso físico del puerto de sí mismo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 En el tiempo de ejecución de Win32, por ejemplo, este método normalmente llama a la función de Win32 `GetCurrentProcessId` para obtener el identificador de proceso físicos.

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)