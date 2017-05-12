---
title: "IDebugApplication::AddStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::AddStackFrameSniffer"
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::AddStackFrameSniffer
Agrega un proveedor de enumerador del marco de pila en esta aplicación.  
  
## Sintaxis  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### Parámetros  
 `pdsfs`  
 \[in\] proveedor de enumerador del marco de pila de Va a agregar a esta aplicación.  
  
 `pdwCookie`  
 \[out\] cookie de que se utiliza para quitar este proveedor de enumerador del marco de pila de la aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Aunque los motores de lenguaje llama normalmente este método para exponer sus marcos de pila el depurador, es posible que otras entidades exponen los marcos de pila.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer \(Interfaz\)](../../winscript/reference/idebugstackframesniffer-interface.md)