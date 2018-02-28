---
title: IDebugApplication (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>IDebugApplication (Interfaz)
Expone métodos de depuración no remota para su uso por hosts y motores de idioma.  
  
 Además de los métodos heredados de `IRemoteDebugApplication`, el `IDebugApplication` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Establece el nombre de la aplicación.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifica al administrador de depuración de proceso que un motor de lenguaje en modo paso a paso está a punto de volver a su llamador.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Hace que la cadena especificada que va a mostrar el IDE de depurador.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Inicia al depurador predeterminado IDE y se asocia una sesión de depuración a esta aplicación, si uno no está ya conectado.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Hace que el subproceso actual se bloquee y envía una notificación del punto de interrupción en el depurador IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Hace que esta aplicación para liberar todas las referencias y entrar en un estado inactivo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Devuelve las marcas de salto actual de la aplicación.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Devuelve el subproceso asociado con el subproceso actualmente en ejecución.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Proporciona acceso asincrónico a una operación de depuración sincrónico determinado.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Agrega un proveedor de enumerador del marco de pila para esta aplicación.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Quita un proveedor de enumerador del marco de pila de esta aplicación.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina si el subproceso de ejecución actual es el subproceso del depurador.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Proporciona un mecanismo para que el llamador ejecutar código en el subproceso del depurador.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crea un nuevo nodo de aplicación que está asociado a un proveedor de documento específico.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Se desencadena un evento genérico para el depurador `IApplicationDebugger` interfaz.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Hace que el subproceso actual se bloquee y envía una notificación del error para el IDE del depurador.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina si un depurador de just-in-time (JIT) está registrado.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina si un depurador JIT está registrado con hosts no inteligente auto-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Agrega un proveedor de contexto de expresión global a esta aplicación.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Quita un proveedor de contexto de expresión global de esta aplicación.|