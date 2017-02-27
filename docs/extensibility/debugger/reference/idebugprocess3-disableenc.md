---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método explícitamente deshabilita editar y Continuar en este proceso \(y todos los programas que contiene\).  Un proveedor de puerto siempre debe devolver `E_NOTIMPL`.  
  
## Sintaxis  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### Parámetros  
 `reason`  
 \[in\]  Un valor de enumeración de [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
> [!NOTE]
>  Un proveedor de puerto siempre debe devolver `E_NOTIMPL`.  
  
## Comentarios  
 Una vez editar y Continuar se deshabilita para un proceso, éste se puede volver a habilitar sólo reiniciando el proceso.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)