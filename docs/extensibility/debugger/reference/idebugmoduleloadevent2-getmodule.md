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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4605b5eab9137fd918238143d8f0453f9f8c54b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065377"
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
