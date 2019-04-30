---
title: IDebugMethodField::EnumArguments | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf62392118ed3ddfb2dfbfca06588f0935f3192d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918726"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crea un enumerador para el tipo de cada argumento necesario para llamar al método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

#### <a name="parameters"></a>Parámetros
 `ppParams`

 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de tipos de argumento. Devuelve un valor null si no hay ningún argumento.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún argumento. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan los tipos de cada parámetro. Llame a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para recuperar información sobre el tipo de cada parámetro.

 Si se necesita el nombre del parámetro junto con el tipo, a continuación, llame a la [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) método.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)