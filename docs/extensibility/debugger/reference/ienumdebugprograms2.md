---
title: "IEnumDebugPrograms2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se enumeran los programas que se ejecutan en la sesión de depuración actual.  
  
## Sintaxis  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para proporcionar una lista de software que es depurados por el OF.  
  
## Notas para los llamadores  
 Visual Studio llama [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obtener esta interfaz.  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) no se usa en Visual Studio.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IEnumDebugPrograms2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un número especificado de programas en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Omite un número especificado de programas en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtiene el número de programas del enumerador.|  
  
## Comentarios  
 Visual Studio utiliza esta interfaz:  
  
-   Rellene la ventana de **Módulos** \(llamando a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) y a continuación [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) en cada programa\).  
  
-   Rellenar la lista de **Adjuntar a procesar** \(llamando a `IDebugProcess2::EnumPrograms` y a continuación [QueryInterface](/visual-cpp/atl/queryinterface) en cada interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para obtener una interfaz de [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) \).  
  
-   Genere una lista de DES que pueda depurar cada programa del proceso \(mediante [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\).  
  
-   Aplicar las actualizaciones de editar y continuar \(ENC\) a cada programa \(llamando a IDebugProcess2:: [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)de EnumPrograms y el llamar\).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)