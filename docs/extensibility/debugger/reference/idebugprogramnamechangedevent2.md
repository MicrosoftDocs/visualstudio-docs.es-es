---
title: "IDebugProgramNameChangedEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugProgramNameChangedEvent2"
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNameChangedEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Envía desde el motor de depuración (DE) para el Administrador de depuración de la sesión (SDM) cuando cambia el nombre de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para informar de que ha cambiado el nombre del programa. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz se debe implementar en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la **IDebugEvent2** interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DE crea y envía este objeto de evento para notificar un cambio de nombre de programa. La DE envía este evento usando el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando. El proveedor de puerto personalizado envía este evento mediante que interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll