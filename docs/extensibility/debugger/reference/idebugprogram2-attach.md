---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Asocia el programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### Parámetros  
 `pCallback`  
 \[in\]  Un objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se utilizará para la notificación de eventos de depuración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  La tabla siguiente se muestran algunos códigos de error posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El programa especificado ya está asociado al depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Una infracción de seguridad producida durante el procedimiento de asociar.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programa de escritorio no se puede asociar el depurador.|  
  
## Comentarios  
 Un motor de depuración \(DE\) nunca llama a este método para asociar un programa.  Si el OF se ejecuta en el espacio de direcciones del programa, se llama al método de [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  Si se ejecuta en la sesión del espacio de direcciones \(SDM\) de administrador, se llama al método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)