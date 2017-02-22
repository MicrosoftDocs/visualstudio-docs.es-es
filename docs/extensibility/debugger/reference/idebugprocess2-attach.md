---
title: "IDebugProcess2::Attach | Microsoft Docs"
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
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Asocia el administrador de depuración de sesión \(SDM\) al proceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### Parámetros  
 `pCallback`  
 \[in\]  Un objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se utiliza para la notificación de eventos de depuración.  
  
 `rgguidSpecificEngines`  
 \[in\]  Una matriz de GUID de los motores de depuración que se utilizarán a los programas de depuración que se ejecutan en el proceso.  Este parámetro puede ser un valor NULL.  Vea las notas de detalles.  
  
 `celtSpecificEngines`  
 \[in\]  El número de motores de depuración en la matriz de `rgguidSpecificEngines` y el tamaño de la matriz de `rghrEngineAttach` .  
  
 `rghrEngineAttach`  
 \[in, out\]  Una matriz de códigos HRESULT devueltos por los motores de depuración.  El tamaño de esta matriz se especifica en el parámetro de `celtSpecificEngines` .  Cada código es normalmente `S_OK` o `S_ATTACH_DEFERRED`.  Este último indica que el OF está asociado actualmente a ningún software.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra otros valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El proceso especificado ya está asociado al depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Una infracción de seguridad producida durante el procedimiento de asociar.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un proceso de escritorio no se puede asociar el depurador.|  
  
## Comentarios  
 Asociar el depurador a un proceso asocia el SDM todos los programas que se ejecutan en ese proceso que se puede depurar por los motores de \(DE\) depuración especificados en la matriz de `rgguidSpecificEngines` .  Establezca el parámetro de `rgguidSpecificEngines` con un valor null o inclusión `GUID_NULL` en la matriz para adjuntar a todos los programas en el proceso.  
  
 Todos los eventos de depuración que aparecen en el proceso se envían al objeto dado de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) .  Se proporciona este objeto de `IDebugEventCallback2` cuando el SDM llama a este método.  
  
## Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)