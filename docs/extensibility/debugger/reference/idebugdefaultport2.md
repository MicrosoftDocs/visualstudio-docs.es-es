---
title: "IDebugDefaultPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "Interfaz IDebugDefaultPort2"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona varios métodos para tener acceso al servidor de un puerto y a las funciones de notificación.  
  
## Sintaxis  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## Notas para los implementadores  
 Visual Studio implementa esta interfaz para representar el puerto de depuración para los programas de acceso.  Un proveedor de puerto puede implementar esta interfaz si controla la depuración remota.  
  
## Notas para los llamadores  
 Un argumento a los métodos de fuentes de la interfaz de [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) esta interfaz.  La llamada [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) también puede obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 Además de los métodos definidos en [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtiene la interfaz de notificación del puerto de este puerto.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtiene la interfaz al servidor que hospeda este puerto.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|determina si este puerto está ejecutando en el equipo local.|  
  
## Comentarios  
 El nombre “`IDebugDefaultPort2`” es un bit de un nombre incorrecto, porque no representa un puerto predeterminado.  Podría ser denominado “IDebugPort3.”  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)