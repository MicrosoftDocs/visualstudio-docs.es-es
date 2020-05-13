---
title: IDebugProgram2::EnumCodePaths ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723034"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera una lista de las rutas de acceso de código para una posición determinada en un archivo de origen.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parámetros
`pszHint`\
[en] La palabra debajo del cursor en la vista **Origen** o **Desensamblado** del IDE.

`pStart`\
[en] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto de código actual.

`pFrame`\
[en] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa el marco de pila asociado con el punto de interrupción actual.

`fSource`\
[en] Distinto de`TRUE`cero ( ) si en`FALSE`la vista **Origen,** o cero ( ) si en la vista **Desensamblado.**

`ppEnum`\
[fuera] Devuelve un objeto [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) que contiene una lista de las rutas de acceso de código.

`ppSafety`\
[fuera] Devuelve un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa un contexto de código adicional que se establecerá como un punto de interrupción en caso de que se omita la ruta de acceso de código elegido. Esto puede suceder en el caso de una expresión booleana con cortocircuito, por ejemplo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una ruta de acceso de código describe el nombre de un método o función que se llamó para llegar al punto actual en la ejecución del programa. Una lista de rutas de acceso de código representa la pila de llamadas.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
