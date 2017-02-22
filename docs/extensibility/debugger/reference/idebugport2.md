---
title: "IDebugPort2 | Microsoft Docs"
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
  - "IDebugPort2"
helpviewer_keywords: 
  - "Interfaz IDebugPort2"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un puerto de depuración en un equipo.  
  
## Sintaxis  
  
```  
IDebugPort2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz para representar un puerto de depuración en un equipo.  
  
 Si el puerto admite el envío de eventos de puerto, también debe implementar la interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> para admitir una interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> que a su vez proporciona la interfaz de [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## Notas para los llamadores  
 Llamadas al resultado de [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) o de [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) esta interfaz, que representa el puerto solicitado.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugPort2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|devuelve el nombre de puerto.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Devuelve el identificador del puerto.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Devuelve la solicitud utilizada para crear un puerto \(si está disponible\).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Devuelve el proveedor de puerto para este puerto.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Devuelve una interfaz al proceso especificado por el identificador de proceso.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Muestra todos los procesos que se ejecutan en un puerto.|  
  
## Comentarios  
 El puerto local proporciona acceso a todos los procesos y programas que se ejecutan en el equipo local.  Otros puertos podrían representar una conexión de cable serie a un dispositivo basado en Windows CE, o una conexión de red a un equipo de no\-DCOM.  La interfaz de `IDebugPort2` se utiliza para buscar el nombre y el identificador de un puerto, enumerar todos procesa la ejecución en el puerto, y proporciona los medios para iniciar y finalizar procesos en el puerto.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)