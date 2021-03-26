---
description: Lo llama un controlador de eventos para recuperar los resultados de un proceso de carga de símbolos.
title: 'IDebugSymbolSearchEvent2:: Getsymbolsearchinfo (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18ca042250d532fe886ac969df5a09bd5d1a49f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081248"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Lo llama un controlador de eventos para recuperar los resultados de un proceso de carga de símbolos.

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
enuncia Un objeto IDebugModule3 que representa el módulo para el que se cargaron los símbolos.

`pbstrDebugMessage`\
[in, out] Devuelve una cadena que contiene los mensajes de error del módulo. Si no hay ningún error, esta cadena solo contendrá el nombre del módulo, pero nunca estará vacío.

> [!NOTE]
> [C++] `pbstrDebugMessage` no puede ser `NULL` y se debe liberar con `SysFreeString` .

`pdwModuleInfoFlags`\
enuncia Combinación de marcas de la enumeración [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) que indica si se cargaron símbolos.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cuando un controlador recibe el evento [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) después de realizar un intento de cargar símbolos de depuración para un módulo, el controlador puede llamar a thismethod para determinar los resultados de esa carga.

## <a name="see-also"></a>Consulte también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
