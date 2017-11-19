---
title: IDebugStopCompleteEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
El motor de depuración (Alemania) puede enviar este evento opcional para el Administrador de sesión de depuración (SDM) cuando un programa se ha detenido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Se trata de una nueva interfaz de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Las versiones anteriores no admitían detención asincrónica.  
  
 [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama el SDM en escenarios de varios procesos o programas múltiples. Cuando un programa envía un evento de detención para la SDM, el SDM solicita otros programas para detener, demasiado.  
  
 Se usa para informar de forma asincrónica el SDM que un programa se ha detenido. Esto es útil para un motor de depuración intérprete, a veces, donde no se ejecuta ningún código en el programa depurado, por lo que [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no puede completarse sincrónicamente. Si desea que un motor de depuración emplean esta notificación asincrónica, debe devolver `S_ASYNC_STOP` de [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll