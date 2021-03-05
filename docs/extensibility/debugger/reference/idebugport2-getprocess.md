---
description: Obtiene el proceso especificado que se ejecuta en un puerto.
title: 'IDebugPort2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f3cf42e4f1316951ee50d110fe79b1191e4dc8e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142861"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Obtiene el proceso especificado que se ejecuta en un puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProcess( 
   AD_PROCESS_ID    ProcessId,
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess( 
   AD_PROCESS_ID      ProcessId,
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parámetros
`ProcessId`\
de Estructura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que especifica el identificador de proceso.

`ppProcess`\
enuncia Devuelve un objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
