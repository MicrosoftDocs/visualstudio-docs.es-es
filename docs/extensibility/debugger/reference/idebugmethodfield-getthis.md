---
description: Obtiene el puntero this (me in Visual Basic) del objeto que contiene el método.
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 662555ec4552aa016b40c1e9c8222992e6cdfd66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076659"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtiene el `this` `Me` puntero (en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) del objeto que contiene el método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parámetros
`ppClass`\
enuncia Devuelve un objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el puntero "this".

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En los lenguajes orientados a objetos, suele haber un puntero implícito a la creación de instancias actual de una clase. Esto se conoce como `this` en C#/c + + y como `Me` en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Consulte también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
