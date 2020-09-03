---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
de Un valor de la enumeración [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) que especifica el tipo de volcado, por ejemplo, Short o Long.

`pszDumpUrl`\
de Dirección URL en la que se va a escribir el volcado. Normalmente, tiene el formato `file://c:\path\filename.ext` , pero puede ser cualquier dirección URL válida.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un volcado de programa normalmente incluiría el marco de pila actual, la propia pila, una lista de los subprocesos que se ejecutan en el programa y, posiblemente, cualquier memoria que posea el programa.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
