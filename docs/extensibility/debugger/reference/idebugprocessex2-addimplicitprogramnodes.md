---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes (método)"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método agrega un nodo de programa para cada motor \(DE\) de depuración especificado.  
  
## Sintaxis  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### Parámetros  
 `guidLaunchingEngine`  
 \[in\]  `GUID` de un OF que debe utilizar para iniciar programas \(y se supone agregar sus propios nodos de programa\).  
  
 `rgguidSpecificEngines`  
 \[in\]  Matriz de s para `GUID`de DES para los nodos del programa se agregarán.  
  
 `celtSpecificEngines`  
 \[in\]  El número de s de `GUID`en la matriz de `rgguidSpecificEngines` .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md) se agregará para cada OF enumerado en `rgguidSpecificEngines`\(excepto el motor que inicia \(según lo especificado en `guidLaunchingEngine`\), que se supone para agregar su propio nodo de programa cuando inicia un programa.  
  
## Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodos de programa](../../../extensibility/debugger/program-nodes.md)