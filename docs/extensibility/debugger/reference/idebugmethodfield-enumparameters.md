---
title: IDebugMethodField::EnumParameters | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9bc7a2049f98c06b83907061cfbee063c810baf
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210330"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crea un enumerador para los parámetros del método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parámetros
`ppParams`\
[out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de parámetros al método; en caso contrario, devuelve un valor null si no hay ningún parámetro.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún parámetro. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan diferentes tipos de parámetros. Llame a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método en cada objeto para determinar exactamente qué tipo de parámetro el objeto representa.

 Un parámetro que incluye su nombre de variable y su tipo. Normalmente, el primer parámetro a un método de clase es el puntero "this".

 Si solo los tipos de los parámetros es necesario, llame a la [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)