---
title: "IDebugAddress2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2"
helpviewer_keywords: 
  - "Interfaz IDebugAddress2"
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona acceso al identificador del proceso que posee el objeto cuya esta interfaz representa dirección.  
  
## Sintaxis  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  Esta interfaz proporciona acceso al identificador del proceso que posee el objeto relacionada con esta dirección.  
  
## Notas para los llamadores  
 utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Métodos de orden vtable  
 además de los métodos heredados de la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera el identificador del proceso que posee el objeto representado por esta interfaz.|  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)