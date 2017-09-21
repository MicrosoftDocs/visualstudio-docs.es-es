---
title: "IEnumDebugCustomAttributes::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Reset"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Reset"
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restablece la secuencia de enumeración al principio.  
  
## Sintaxis  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Después de que se llame a este método, la siguiente llamada al método de [Siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) devuelve el primer elemento de la enumeración.  
  
## Vea también  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)