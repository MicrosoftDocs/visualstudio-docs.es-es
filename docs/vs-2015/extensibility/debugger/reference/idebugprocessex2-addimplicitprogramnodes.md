---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b416fdfd3c3a08d028bb01945f2ceb02ae5f8e3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733586"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método agrega un nodo de programa para cada motor de depuración (DE) especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregarán para cada DE enumerada en `rgguidSpecificEngines`, excepto el motor de inicio (como se indica en `guidLaunchingEngine`), que se supone que agregue su propio nodo programa cuando inicia un programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md)

