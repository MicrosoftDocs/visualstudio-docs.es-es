---
description: Recupera una lista de las rutas de acceso de código para una posición determinada en un archivo de código fuente.
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c647379d0b72832a4068d720846f8a9331f9b939
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159970"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera una lista de las rutas de acceso de código para una posición determinada en un archivo de código fuente.

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
de Palabra bajo el cursor en la vista de **origen** o **Desensamblado** del IDE.

`pStart`\
de Un objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa el contexto de código actual.

`pFrame`\
de Un objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa el marco de pila asociado al punto de interrupción actual.

`fSource`\
de Es distinto de cero ( `TRUE` ) si está en la vista de **código fuente** o cero ( `FALSE` ) si está en la vista **Desensamblado** .

`ppEnum`\
enuncia Devuelve un objeto [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) que contiene una lista de las rutas de acceso del código.

`ppSafety`\
enuncia Devuelve un objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa un contexto de código adicional que se va a establecer como punto de interrupción en caso de que se omita la ruta de acceso del código elegido. Esto puede ocurrir en el caso de una expresión booleana de cortocircuito, por ejemplo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una ruta de acceso de código describe el nombre de un método o función que se llamó para llegar al punto actual en la ejecución del programa. Una lista de rutas de acceso de código representa la pila de llamadas.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
