---
title: "IDebugApplication::DebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::DebugOutput"
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::DebugOutput
Hace que la cadena con que se muestre por el entorno de desarrollo integrado \(IDE\) del depurador.  
  
## Sintaxis  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### Parámetros  
 `pstr`  
 \[in\] cadena a mostrar en el depurador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método permite que un motor de lenguaje implementa compatibilidad lenguaje específico del resultado de depuración.  La cadena se muestra normalmente en la ventana de salida del depurador.  
  
 Este método hace que `IApplicationDebugger::onDebugOutput` que se va a llamar.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)