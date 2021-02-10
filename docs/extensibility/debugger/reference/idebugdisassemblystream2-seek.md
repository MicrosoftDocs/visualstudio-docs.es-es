---
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3223f454fbf775b6aa11512c20fc63f8c224ade7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944633"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Mueve el puntero de lectura en el flujo del desensamblado un número determinado de instrucciones relativas a una posición especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parámetros
`dwSeekStart`\
de Un valor de la enumeración [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) que especifica la posición relativa para comenzar el proceso de búsqueda.

`pCodeContext`\
de Objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa el contexto de código con el que la operación de búsqueda es relativa. Este parámetro solo se usa si `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; de lo contrario, este parámetro se omite y puede ser un valor null.

`uCodeLocationId`\
de Identificador de ubicación de código con el que la operación de búsqueda es relativa. Este parámetro se usa si `dwSeekStart`  =  `SEEK_START_CODELOCID` ; en caso contrario, este parámetro se omite y se puede establecer en 0. Vea la sección Comentarios del método [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obtener una descripción de un identificador de ubicación de código.

`iInstructions`\
de Número de instrucciones que se van a mover en relación con la posición especificada en `dwSeekStart` . Este valor puede ser negativo para moverse hacia atrás.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si la posición de búsqueda fue hasta un punto más allá de la lista de instrucciones disponibles. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Si la búsqueda estaba en una posición antes del principio de la lista, la posición de lectura se establece en la primera instrucción de la lista. Si la consulta va a una posición después del final de la lista, la posición de lectura se establece en la última instrucción de la lista.

## <a name="see-also"></a>Vea también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
