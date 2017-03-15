---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método determina si el proveedor de puerto puede conservar los puertos \(escribiéndolos en disco\) entre las invocaciones del depurador.  
  
## Sintaxis  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### Parámetros  
 Ninguno.  
  
## Valor devuelto  
 `S_OK` si los puertos se pueden almacenar, o `S_FALSE` para indicar que los puertos no pueden guardarse.  
  
## Comentarios  
 Si el proveedor de puerto puede conservar los puertos, debe hacerlo cuando se destruye a continuación recargarlos cuando se crean instancias de nuevo.  
  
## Vea también  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)