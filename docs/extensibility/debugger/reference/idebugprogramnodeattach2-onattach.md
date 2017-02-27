---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Asocia el programa asociado o deja el proceso de asociar al método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## Sintaxis  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### Parámetros  
 `guidProgramId`  
 \[in\]  `GUID` a la asignación al programa asociado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si se llama al método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Se llama a este método durante la operación, antes de que se llame al método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  El método de `OnAttach` puede realizar el propio proceso de asociación \(en este caso, este método devuelve `S_FALSE`\) o diferir el proceso de asociar al método de `IDebugEngine2::Attach` \(método de `OnAttach` devuelve `S_OK`\).  En cualquier evento, el método de `OnAttach` puede establecer `GUID` del programa que se depura a `GUID`especificado.  
  
## Vea también  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)