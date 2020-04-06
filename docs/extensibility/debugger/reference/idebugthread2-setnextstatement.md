---
title: IDebugThread2::SetNextStatement ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718652"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Establece el puntero de instrucción actual en el contexto de código especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parámetros
`pStackFrame`\
Reservado para uso futuro; establecido en un valor nulo.

`pCodeContext`\
[en] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que describe la ubicación de código a punto de ejecutarse y su contexto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran otros valores posibles.

|Value|Descripción|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|La siguiente instrucción no puede estar en un marco de pila más profundo en la pila de marcos.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|La siguiente instrucción no está asociada a ningún fotograma de la pila.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Algunos motores de depuración no pueden establecer la siguiente instrucción después de una excepción.|

## <a name="remarks"></a>Observaciones
 El puntero de instrucción indica la siguiente instrucción o instrucción que se va a ejecutar. Este método se utiliza para reintentar una línea de código fuente o para forzar la ejecución para continuar en otra función, por ejemplo.

## <a name="see-also"></a>Vea también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
