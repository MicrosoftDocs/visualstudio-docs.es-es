---
title: IDebugMethodField::EnumParameters ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727197"
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
[fuera] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de parámetros para el método; de lo contrario, devuelve un valor nulo si no hay parámetros.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay parámetros. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa diferentes tipos de parámetros. Llame a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método en cada objeto para determinar exactamente qué tipo de parámetro representa el objeto.

 Un parámetro incluye tanto su nombre de variable como su tipo. El primer parámetro de un método de clase suele ser el puntero "this".

 Si solo se necesitan los tipos de los parámetros, llame a la [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
