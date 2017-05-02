---
title: "IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveStackFrameSniffer"
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveStackFrameSniffer
Quita un proveedor de enumerador del marco de pila de esta aplicación.  
  
## Sintaxis  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### Parámetros  
 `dwCookie`  
 \[in\] la cookie de El devuelto por el método de `AddStackFrameSniffer` cuando el proveedor de enumerador del marco de pila se agregó.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El método de `RemoveStackFrameSniffer` quita un proveedor de enumerador del marco de pila de esta aplicación.  
  
## Vea también  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer \(Interfaz\)](../../winscript/reference/idebugstackframesniffer-interface.md)