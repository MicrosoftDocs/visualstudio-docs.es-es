---
title: IDebugBeforeSymbolSearchEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ec023384ab95e72d0341fb728eb0fd6a4f58480
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
El motor de depuración (Alemania) envía esta interfaz para el Administrador de sesión de depuración (SDM) para establecer el estado de mensaje en la barra durante la carga de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz cuando se debe establecer el mensaje de la barra de estado durante la carga de símbolos. Esta interfaz se implementa únicamente por los motores de depuración que funcionan con o que forman parte de los intérpretes de secuencias de comandos. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz (usa el SDM **QueryInterface** para tener acceso a la **IDebugEvent2** interfaz).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento cuando se debe establecer el mensaje de la barra de estado durante la carga de símbolos. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugBeforeSymbolSearchEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera el nombre del módulo que se está depurando.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll