---
title: "IDebugDefaultPort2::GetPortNotify | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::GetPortNotify"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetPortNotify"
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método obtiene una interfaz de [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) para este puerto.  
  
## Sintaxis  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```c#  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### Parámetros  
 `ppPortNotify`  
 \[out\]  un objeto de [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Normalmente, el método de `QueryInterface` se llama en el objeto que implementa la interfaz de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) para obtener una interfaz de [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .  Sin embargo, hay circunstancias en las que la interfaz deseada se implementa en un objeto diferente.  Este método oculta esas circunstancias y devuelve la interfaz de `IDebugPortNotify2` de objeto más adecuado.  
  
## Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)