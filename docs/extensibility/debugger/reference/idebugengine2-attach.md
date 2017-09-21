---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Asocia un motor de depuración \(DE\) a un programa o a programas.  Llamado por el administrador de depuración de la sesión \(SDM\) cuando el OF se ejecuta en proceso en el SDM.  
  
## Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### Parámetros  
 `pProgram`  
 \[in\]  Matriz de los objetos de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) a los que representa los programas que se va a asociar.  Éstos son programas de puerto.  
  
 `rgpProgramNodes`  
 \[in\]  Matriz de los objetos de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representan nodos de programa, una para cada programa.  Los nodos del programa en esta matriz representan los mismos programas que en `pProgram`.  Se proporcionan a los nodos del programa de modo que el OF pueda identificar programas para asociar.  
  
 `celtPrograms`  
 \[in\]  Número de software o de nodos de programa en matrices de `pProgram` y de `rgpProgramNodes` .  
  
 `pCallback`  
 \[in\]  El objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se utilizará para enviar eventos de depuración al SDM.  
  
 `dwReason`  
 \[in\]  Un valor de enumeración de [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica la razón de adjuntar estos programas.  Para obtener más información, vea la sección Comentarios.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Hay tres razones de asociar un programa, como sigue:  
  
-   `ATTACH_REASON_LAUNCH` indica que el OF se está asociando el programa porque el usuario arrancó el proceso que lo contiene.  
  
-   `ATTACH_REASON_USER` indica que el usuario explícitamente ha solicitado el OF asociar un programa \(o el proceso que contiene un programa\).  
  
-   `ATTACH_REASON_AUTO` indica que el OF está adjuntando un programa concreto porque está depurando ya otros programas en un proceso determinado.  También se denomina asociación automática.  
  
 Cuando se llama a este método, el OF necesita enviar estos eventos en orden:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(si no se ha enviado aún para una instancia determinada del motor de depuración\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Además, si la razón de adjuntar es `ATTACH_REASON_LAUNCH`, el OF necesita devolver el evento de [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .  
  
 Una vez que el OF obtiene el objeto de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondiente al programa que se está depurando, se puede consultar para cualquier interfaz privada.  
  
 Antes de llamar a los métodos de un nodo de programa en la matriz especificada por `pProgram` o `rgpProgramNodes`, la suplantación, si existe, se debe habilitar en la interfaz de `IDebugProgram2` que representa el nodo del programa.  normalmente, sin embargo, este paso no es necesario.  Para obtener más información, vea [Problemas de seguridad](../../../extensibility/debugger/security-issues.md).  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)