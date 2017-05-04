---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
Proporciona un mecanismo para el llamador para ejecutar código en el subproceso del depurador.  
  
## Sintaxis  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Parámetros  
 `pptc`  
 \[in\] objeto de la llamada.  
  
 `dwParam1`  
 \[in\] parámetro de Tareas para pasar a `IDebugThreadCall::ThreadCallHandler` el método.  
  
 `dwParam2`  
 \[in\] parámetro de Segundo para pasar a `IDebugThreadCall::ThreadCallHandler` el método.  
  
 `dwParam3`  
 \[in\] parámetro de Third para pasar a `IDebugThreadCall::ThreadCallHandler` el método.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Los motores y hosts de lenguaje suelen utilizar este método para implementar objetos libre\- roscados encima de las únicas implementaciones roscadas.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall \(Interfaz\)](../../winscript/reference/idebugthreadcall-interface.md)