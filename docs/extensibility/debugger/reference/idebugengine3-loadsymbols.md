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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43651baac29b3904b9bc12d8d4b965ca1cd8e3ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066186"
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
