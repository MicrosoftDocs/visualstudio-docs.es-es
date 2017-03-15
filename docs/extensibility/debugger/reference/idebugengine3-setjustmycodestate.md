---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método informa al motor de depuración de la información de estado de JustMyCode.  
  
## Sintaxis  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### Parámetros  
 `fUpdate`  
 \[in\]  Cero \(`TRUE`\) para actualizar la información actual, cero \(`FALSE`\) para restaurar toda la información \(que omite nada establecida previamente\).  
  
 `dwModules`  
 \[in\]  número de estructuras de información en `rgJMCSpec.`  
  
 `rgJMCSpec`  
 \[in\]  Matriz de estructuras de [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) a utilizar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Comentarios  
 JustMyCode es el concepto de depurar sólo el código correspondiente a un usuario y a omitir todo el código intermedio como sistema código\-uniforme si el código fuente disponible para el código del sistema.  
  
## Vea también  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)