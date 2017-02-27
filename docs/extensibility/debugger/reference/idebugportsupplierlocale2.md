---
title: "IDebugPortSupplierLocale2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugPortSupplierLocale2"
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Proporciona compatibilidad con la configuración regional para un proveedor de puerto.  
  
## Sintaxis  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz para establecer la configuración regional.  
  
## Métodos  
 La tabla siguiente se muestran los métodos **de IDebugPortSupplierLocale2**.  
  
|Método|Descripción|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Establece la configuración regional del proveedor de puerto.|  
  
## Requisitos  
 encabezado: Portpriv.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)