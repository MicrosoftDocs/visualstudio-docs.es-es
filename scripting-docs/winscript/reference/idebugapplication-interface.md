---
title: "IDebugApplication (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication (interfaz)"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication (Interfaz)
Expone métodos de depuración de no remoto para uso de los motores y hosts del lenguaje.  
  
 Además de los métodos heredados de `IRemoteDebugApplication`, la interfaz `IDebugApplication` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Establece el nombre de la aplicación.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifica al administrador de depuración que un motor de lenguaje en modo paso a paso está a punto de volver al llamador.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Hace que la cadena con que se muestre el depurador el IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Iniciar el depurador predeterminado el IDE y asocia a una sesión de depuración a esta aplicación, si no ya está asociado.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Hace que el subproceso actual para bloquear y envía una notificación de punto de interrupción al depurador el IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Provoca esta aplicación para liberar todas las referencias y para entrar en un estado inactivo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Devuelve marcas actuales de la interrupción de la aplicación.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Devuelve el subproceso asociado al subproceso que se está ejecutando actualmente.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Proporciona acceso asincrónico a una operación sincrónica determinada de depuración.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Agrega un proveedor de enumerador del marco de pila en esta aplicación.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Quita un proveedor de enumerador del marco de pila de esta aplicación.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina si el subproceso actual de ejecución es el subproceso del depurador.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Proporciona un mecanismo para el llamador para ejecutar código en el subproceso del depurador.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crea un nodo de aplicación asociado a un proveedor de documento concreto.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Desencadena un evento genérico a la interfaz de `IApplicationDebugger` del depurador.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Hace que el subproceso actual para bloquear y envía una notificación de error al depurador el IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina si se registran en un depurador just\-in\-time de \(JIT\).|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina si un depurador JIT es host mudos registrados de la auto\- depuración.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Agrega un proveedor global del contexto de la expresión de esta aplicación.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Quita un proveedor global del contexto de la expresión de esta aplicación.|