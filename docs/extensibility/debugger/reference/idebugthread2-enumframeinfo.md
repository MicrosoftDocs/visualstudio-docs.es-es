---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera una lista de los marcos de pila para este subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### Parámetros  
 `dwFieldSpec`  
 \[in\]  Una combinación de marcadores de enumeración de [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica qué campos de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) se deben completar.  Especifique el marcador de `FIF_FUNCNAME_FORMAT` para dar formato al nombre de función en una sola.  
  
 `nRadix`  
 \[in\]  Base utilizada para dar formato a la información numérica en el enumerador.  
  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que contiene una lista de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que describen el marco de pila.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los cuadros de subproceso en orden, con el marco actual enumerado primero y más antiguo cuadro enumerado por última vez.  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)