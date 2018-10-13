---
title: IDebugStopCompleteEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e30b59968fb8eca14d462ce34d12378132771b68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195213"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

El motor de depuración (DE) puede enviar este evento opcional para el Administrador de depuración de la sesión (SDM) cuando se ha detenido un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Se trata de una nueva interfaz para [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Las versiones anteriores no eran compatibles con la detención asincrónica.  
  
 [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama el SDM en escenarios de varios procesos o de varios programas. Cuando un programa envía un evento de detención en el SDM, el SDM solicita otros programas para detener, demasiado.  
  
 Se utiliza para informar de forma asincrónica el SDM que se ha detenido un programa. Esto es útil para un motor de depuración del intérprete, a veces, donde no se ejecuta ningún código dentro del programa depurado, por lo que [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no se puede completar de forma sincrónica. Si un motor de depuración desea emplear esta notificación asincrónica, debe devolver `S_ASYNC_STOP` desde [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

