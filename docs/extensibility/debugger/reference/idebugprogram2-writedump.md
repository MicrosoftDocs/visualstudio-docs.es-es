---
description: Escribe un volcado en un archivo.
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8eca50eb6e828841a247ed51d7f73f61cb63e0e9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084433"
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

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
