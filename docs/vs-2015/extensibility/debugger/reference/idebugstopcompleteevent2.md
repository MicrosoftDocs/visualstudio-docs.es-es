---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546928"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

El motor DE depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando se ha detenido un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Se trata de una nueva interfaz para [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Las versiones anteriores no admiten la detención asincrónica.  
  
 El SDM llama a [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) en escenarios de varios procesos o de varios programas. Cuando un programa envía un evento de detención al SDM, el SDM solicita también que se detengan otros programas.  
  
 Se utiliza para informar de forma asincrónica al SDM de que se ha detenido un programa. Esto resulta útil para un motor de depuración de intérprete, donde a veces no se ejecuta código dentro del programa depurado, por lo que no se puede completar la [detención](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) de forma sincrónica. Si un motor de depuración desea emplear esta notificación asincrónica, debe devolver `S_ASYNC_STOP` de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
