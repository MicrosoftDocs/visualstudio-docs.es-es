---
title: IDebugApplication (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3483bea94d7a53fabf3f552df97a681307b885c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349730"
---
# <a name="idebugapplication-interface"></a>IDebugApplication (Interfaz)
Expone métodos de depuración no remota para su uso por los hosts y motores de lenguaje.  
  
 Además de los métodos heredados de `IRemoteDebugApplication`, el `IDebugApplication` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Establece el nombre de la aplicación.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifica al administrador de depuración de proceso que un motor de lenguaje en modo paso a paso está a punto de volver a su llamador.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Hace que la cadena especificada que va a mostrar el IDE del depurador.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Se inicia el IDE del depurador predeterminado y adjunta una sesión de depuración para esta aplicación, si uno no está ya conectado.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Hace que el subproceso actual se bloquea y envía una notificación del punto de interrupción en el IDE del depurador.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Hace que esta aplicación para liberar todas las referencias y entrar en un estado inactivo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Devuelve las marcas de interrupción actual de la aplicación.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Devuelve el subproceso asociado al subproceso que se está ejecutando.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Proporciona acceso asincrónico a una operación de depuración sincrónica determinada.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Agrega un proveedor de enumerador del marco de pila para esta aplicación.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Quita un proveedor de enumerador del marco de pila de esta aplicación.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina si el subproceso de ejecución actual es el subproceso del depurador.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Proporciona un mecanismo para que el llamador ejecutar código en el subproceso del depurador.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crea un nuevo nodo de la aplicación que está asociado con un proveedor de documento específico.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Desencadena un evento genérico para el depurador `IApplicationDebugger` interfaz.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Hace que el subproceso actual se bloquea y envía una notificación del error para el IDE del depurador.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina si un depurador de just-in-time (JIT) está registrado.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina si un depurador JIT está registrado con hosts tontos auto-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Agrega un proveedor de contexto de expresión global a esta aplicación.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Quita un proveedor de contexto de expresión global de esta aplicación.|