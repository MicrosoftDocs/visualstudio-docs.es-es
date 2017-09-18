---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Llama a la función y devuelve el valor resultante como object.  
  
## Sintaxis  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### Parámetros  
 `ppParams`  
 \[in\]  Matriz de los objetos de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa los parámetros de entrada.  Cada uno de estos parámetros se creó utilizando uno de los métodos Create en esta interfaz.  
  
 `dwParams`  
 \[in\]  El número de parámetros en la matriz de `ppParams` .  
  
 `dwEvalFlags`  
 \[in\]  Una combinación de marcadores de enumeración de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifican cómo la evaluación debe realizar.  
  
 `dwTimeout`  
 \[in\]  Especifica el tiempo máximo, en milisegundos, de esperar antes de volver de este método.  uso **Infinito** de esperar indefinidamente.  
  
 `ppResult`  
 \[out\]  Devuelve **un IDebugObject** que representa el valor de la función como un objeto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)