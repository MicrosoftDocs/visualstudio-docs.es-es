---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b75ef50107b44de8de6f65c5c4c9c6827e13426e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309500"
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
[in] El `GUID` de una DE que se utiliza para iniciar programas (y se supone que para agregar sus propios nodos de programa).

`rgguidSpecificEngines`\
[in] Matriz de `GUID`s de DEs para el programa que se agregarán los nodos.

`celtSpecificEngines`\
[in] El número de `GUID`s en el `rgguidSpecificEngines` matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
- [Nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregarán para cada DE enumerada en `rgguidSpecificEngines`, excepto el motor de inicio (como se indica en `guidLaunchingEngine`), que se supone que agregue su propio nodo programa cuando inicia un programa.

## <a name="see-also"></a>Vea también
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nodos de programa](../../../extensibility/debugger/program-nodes.md)