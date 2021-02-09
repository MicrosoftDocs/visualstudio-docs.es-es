---
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961aaf45478f25ed8eb55d8eda91a5c4eafc4dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852952"
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

## <a name="remarks"></a>Notas
 Este método se usa si el puntero representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apunta a un tipo primitivo o a una matriz simple de tipos primitivos (es decir, una matriz que se puede representar mediante una secuencia simple de bytes).

## <a name="see-also"></a>Vea también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
