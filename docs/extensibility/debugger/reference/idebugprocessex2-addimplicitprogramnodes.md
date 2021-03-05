---
description: Este método agrega un nodo de programa para cada motor de depuración (DE) especificado.
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3a4c6446c2106d79dd14fc0378fc848eac3df18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159996"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Este método agrega un nodo de programa para cada motor de depuración (DE) especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parámetros
`guidLaunchingEngine`\
de `GUID` De un de que se va a usar para iniciar programas (y se supone que agrega sus propios nodos de programa).

`rgguidSpecificEngines`\
de Matriz de objetos `GUID` de des para los que se agregarán nodos de programa.

`celtSpecificEngines`\
de Número de `GUID` s de la `rgguidSpecificEngines` matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
- Los [nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregarán para cada uno de los enumerados en `rgguidSpecificEngines` , excluido el motor de inicio (como se indica en `guidLaunchingEngine` ), que se supone que agrega su propio nodo de programa cuando inicia un programa.

## <a name="see-also"></a>Consulte también
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nodos de programa](../../../extensibility/debugger/program-nodes.md)
