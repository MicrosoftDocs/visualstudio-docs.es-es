---
title: IDebugDisassemblyStream2::Buscar Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732086"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Mueve el puntero de lectura en la secuencia de desensamblado un número determinado de instrucciones con respecto a una posición especificada.

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
[en] Valor de la [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumeración que especifica la posición relativa para iniciar el proceso de búsqueda.

`pCodeContext`\
[en] El [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto de código que la operación de búsqueda es relativa a. Este parámetro sólo `dwSeekStart`  =  `SEEK_START_CODECONTEXT`se utiliza si ; de lo contrario, este parámetro se omite y puede ser un valor nulo.

`uCodeLocationId`\
[en] Identificador de ubicación de código con el que se trata la operación de búsqueda. Este parámetro se `dwSeekStart`  =  `SEEK_START_CODELOCID`utiliza si ; de lo contrario, este parámetro se omite y se puede establecer en 0. Consulte la sección Comentarios para el [Método GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obtener una descripción de un identificador de ubicación de código.

`iInstructions`\
[en] El número de instrucciones que se deben `dwSeekStart`mover en relación con la posición especificada en . Este valor puede ser negativo para retroceder.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si la posición de búsqueda fue a un punto más allá de la lista de instrucciones disponibles. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si la búsqueda era a una posición antes del comienzo de la lista, la posición de lectura se establece en la primera instrucción de la lista. Si el ver era en una posición después del final de la lista, la posición de lectura se establece en la última instrucción de la lista.

## <a name="see-also"></a>Vea también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
