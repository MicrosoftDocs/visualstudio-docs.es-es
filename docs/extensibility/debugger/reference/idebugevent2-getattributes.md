---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 140b47af958e8f4623dd5921aa6046926737cf38
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677687"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtiene los atributos de este evento de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

#### <a name="parameters"></a>Parámetros
 `pdwAttrib`

 [out] Una combinación de marcas de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz es común a todos los eventos. Este método describe el tipo de evento; Por ejemplo, es el evento sincrónica o asincrónica y es un evento de detención.

## <a name="see-also"></a>Vea también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)