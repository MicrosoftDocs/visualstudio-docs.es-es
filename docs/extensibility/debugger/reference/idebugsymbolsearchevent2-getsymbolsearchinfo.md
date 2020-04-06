---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718887"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Llamado por un controlador de eventos para recuperar resultados sobre un proceso de carga de símbolos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parámetros
`pModule`\
[fuera] Un IDebugModule3 objeto que representa el módulo para el que se cargaron los símbolos.

`pbstrDebugMessage`\
[adentro, fuera] Devuelve una cadena que contiene los mensajes de error del módulo. Si no hay ningún error, esta cadena solo contendrá el nombre del módulo, pero nunca está vacía.

> [!NOTE]
> [C++] `pbstrDebugMessage` no `NULL` puede ser y `SysFreeString`debe ser liberado con .

`pdwModuleInfoFlags`\
[fuera] Una combinación de indicadores de la [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) enumeración que indica si se han cargado símbolos.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cuando un controlador recibe el [evento IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) después de intentar cargar símbolos de depuración para un módulo, el controlador puede llamar a este método para determinar los resultados de esa carga.

## <a name="see-also"></a>Vea también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
