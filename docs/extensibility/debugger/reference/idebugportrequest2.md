---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "Interfaz IDebugPortRequest2"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz describe un puerto.  Esta descripción se utiliza para agregar el puerto a un proveedor de puerto.  
  
## Sintaxis  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## Notas para los implementadores  
 Visual Studio implementará normalmente esta interfaz actual de obtener un puerto de depuración de un proveedor de puerto.  
  
## Notas para los llamadores  
 Esta interfaz se pasa en [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para crear un puerto de depuración.  Una llamada a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) devuelve esta interfaz, que representa la solicitud utilizada para crear el puerto en primer lugar.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugPortRequest2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtiene el nombre del puerto para crear.|  
  
## Comentarios  
 Un motor de depuración no interactúa normalmente con un proveedor de puerto y no tendrá ningún uso en esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)