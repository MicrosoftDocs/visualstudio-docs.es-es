---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject (método)"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### Parámetros  
 `ppObject`  
 \[out\]  Devuelve un objeto de [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) que representa el objeto administrado recién creado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  Devuelve E\_FAIL si este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) no representa una instancia de la clase administrada de valor.  
  
## Comentarios  
 Este objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) debe representar una instancia de la clase administrada de valor, como una instancia de `System.Decimal` .  Tener una copia local, la sobrecarga de llamar a [Evaluar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) se elimina.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)