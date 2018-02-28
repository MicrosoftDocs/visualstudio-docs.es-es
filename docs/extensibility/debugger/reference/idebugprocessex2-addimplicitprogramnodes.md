---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: adc3f54188e57bd5453703c0aa68fe281fd2ca5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Este método agrega un nodo de programa para cada motor de depuración (Alemania) especificado.  
  
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
 [in] El `GUID` de un Alemania que va a usar para iniciar programas (y se supone que para agregar su propio programa de nodos).  
  
 `rgguidSpecificEngines`  
 [in] Matriz de `GUID`s de DEs para el programa que se agregarán los nodos.  
  
 `celtSpecificEngines`  
 [in] El número de `GUID`s en el `rgguidSpecificEngines` matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregarán para cada Alemania se enumeran en `rgguidSpecificEngines`, sin incluir el motor de lanzamiento (como se indica en `guidLaunchingEngine`), que se supone que agregue su propio nodo de programa cuando se inicia un programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md)