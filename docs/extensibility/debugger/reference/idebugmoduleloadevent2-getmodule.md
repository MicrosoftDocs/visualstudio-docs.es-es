---
description: Obtiene el módulo que se está cargando o descargando.
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e44268dcf4ab79e99bd1bdf5a996ae18762e139
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149839"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtiene el módulo que se está cargando o descargando.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parámetros
`pModule`\
enuncia Devuelve un objeto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa el módulo que se carga o descarga.

`pbstrDebugMessage`\
[in, out] Devuelve un mensaje opcional que describe este evento. Si este parámetro es un valor nulo, no se solicita ningún mensaje.

`pbLoad`\
[in, out] Distinto de cero ( `TRUE` ) si el módulo se está cargando y cero ( `FALSE` ) si el módulo se está descargando. Si este parámetro es un valor nulo, no se solicita ningún Estado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
