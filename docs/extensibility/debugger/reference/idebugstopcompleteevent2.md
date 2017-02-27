---
title: "IDebugStopCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugStopCompleteEvent2"
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) puede enviar este evento opcional al administrador \(SDM\) de la depuración de sesión cuando un programa ha detenido.  
  
## Sintaxis  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 Ésta es una nueva interfaz para [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)].  Las versiones anteriores no admitidos detener asincrónico.  
  
 [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama el SDM en varios procesos o multiprograma escenarios.  Cuando un programa envía un evento que detiene el SDM, el SDM solicita otros programas detener, también.  
  
 Se utiliza de forma asincrónica para informar al SDM que un programa ha detenido.  Esto es útil para un motor de depuración el intérprete, donde ningún código ejecuta a veces dentro de programas depurados, por lo que [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no se puede completar de forma sincrónica.  Si un motor de depuración desea emplear esta notificación asincrónica, debe devolver `S_ASYNC_STOP` de [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll