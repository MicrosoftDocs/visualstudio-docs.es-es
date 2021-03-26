---
description: Obtiene el valor al que se apunta como una serie de bytes consecutivos.
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087631"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Obtiene el valor al que se apunta como una serie de bytes consecutivos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parámetros
`dwStart`\
de Desplazamiento, en bytes, desde el inicio del objeto al que se señala.

`dwCount`\
de Número de bytes que se van a recuperar.

`pBytes`\
[in, out] Matriz que se rellena con el valor como una serie de bytes consecutivos, comenzando en el desplazamiento especificado desde el objeto al que se señala.

`pdwBytes`\
enuncia Devuelve el número de bytes recuperados realmente.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método se usa si el puntero representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apunta a un tipo primitivo o a una matriz simple de tipos primitivos (es decir, una matriz que se puede representar mediante una secuencia simple de bytes).

## <a name="see-also"></a>Consulte también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
