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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725517"
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

## <a name="see-also"></a>Vea también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
