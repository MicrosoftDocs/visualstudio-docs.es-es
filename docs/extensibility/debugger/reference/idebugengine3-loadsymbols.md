---
description: Carga (según sea necesario) símbolos para todos los módulos que está depurando este motor de depuración.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153812"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Carga (según sea necesario) símbolos para todos los módulos que está depurando este motor de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 De esta forma se cargan símbolos de depuración para todos los módulos a los que hace referencia este motor de depuración. Los símbolos solo se cargan si aún no se han cargado. Los símbolos se buscan en las rutas de acceso establecidas por una llamada a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Consulte también
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
