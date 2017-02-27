---
title: "IDebugPortPicker::SetSite | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker::SetSite"
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

establece el proveedor de servicios.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```c#  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### Parámetros  
 `pSP`  
 \[in\]  Referencia a la interfaz del proveedor de servicios.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llamará a este método antes de llamar a cualquier otro método.  
  
## Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)