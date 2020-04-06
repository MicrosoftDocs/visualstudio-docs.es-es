---
title: IDebugProgram2::WriteDump ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722740"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Escribe un volcado en un archivo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parámetros
`DumpType`\
[en] Valor de la enumeración [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) que especifica el tipo de volcado, por ejemplo, corto o largo.

`pszDumpUrl`\
[en] La dirección URL en la que se escribirá el volcado. Normalmente, esto es en `file://c:\path\filename.ext`forma de , pero puede ser cualquier dirección URL válida.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un volcado de programa normalmente incluiría el marco de pila actual, la pila en sí, una lista de los subprocesos que se ejecutan en el programa y, posiblemente, cualquier memoria que el programa posea.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
