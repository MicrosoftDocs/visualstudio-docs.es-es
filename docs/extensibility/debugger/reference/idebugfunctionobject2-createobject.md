---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un objeto que utilice un constructor con valores de marcador de evaluación y un valor de tiempo de espera.  
  
## Sintaxis  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### Parámetros  
 `pConstructor`  
 \[in\]  Un objeto de [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa el constructor del objeto que se va a crear.  
  
 `dwArgs`  
 \[in\]  El número de parámetros en la matriz de `pArg` .  Representa el número de parámetros pasados al constructor.  
  
 `pArgs`  
 \[in\]  Matriz de los objetos de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa los parámetros pasados al constructor.  
  
 `dwEvalFlags`  
 \[in\]  Una combinación de marcadores de enumeración de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifican cómo la evaluación debe realizar.  
  
 `dwTimeout`  
 \[in\]  hora máxima, en milisegundos, de esperar antes de volver de este método.  uso **Infinito** de esperar indefinidamente.  
  
 `ppObject`  
 \[out\]  Devuelve **un IDebugObject** que representa el objeto recién creado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llame a este método para crear el objeto que representa una instancia de una clase, u otro tipo complejo que requiere un constructor, que es un parámetro.  
  
## Vea también  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)