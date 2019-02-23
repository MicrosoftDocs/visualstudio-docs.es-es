---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02ee13b62a2238624f1c6d42c52bf67db2ceaae4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710414"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crea un objeto de cadena que tiene la longitud especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parámetros
 `pcstrString`

 [in] El valor de cadena para el objeto de cadena.

 `uiLength`

 [in] La longitud de la cadena en bytes.

 `ppObject`

 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el objeto de cadena recién creado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)