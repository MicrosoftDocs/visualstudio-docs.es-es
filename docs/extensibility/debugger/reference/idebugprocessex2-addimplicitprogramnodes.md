---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6203b12defbe70d3807508953d85f39ff725a746
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693531"
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

#### <a name="parameters"></a>Parámetros
 `guidLaunchingEngine`

 [in] El `GUID` de una DE que se utiliza para iniciar programas (y se supone que para agregar sus propios nodos de programa).

 `rgguidSpecificEngines`

 [in] Matriz de `GUID`s de DEs para el programa que se agregarán los nodos.

 `celtSpecificEngines`

 [in] El número de `GUID`s en el `rgguidSpecificEngines` matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
- [Nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregarán para cada DE enumerada en `rgguidSpecificEngines`, excepto el motor de inicio (como se indica en `guidLaunchingEngine`), que se supone que agregue su propio nodo programa cuando inicia un programa.

## <a name="see-also"></a>Vea también
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nodos de programa](../../../extensibility/debugger/program-nodes.md)