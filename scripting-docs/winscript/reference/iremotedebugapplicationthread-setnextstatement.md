---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
Ejecución de las ventajas para continuar lo más cercano posible al contexto determinado de código, en el contexto del cuadro especificado.  
  
## Sintaxis  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### Parámetros  
 `pStackFrame`  
 \[in\] objeto de marco de pila de El.  Este argumento puede ser NULL, que implica el marco de pila actual se debe utilizar.  
  
 `pCodeContext`  
 \[in\] contexto de código se.  Este argumento puede ser NULL, que implica el contexto del código de la actual se debe utilizar.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método fuerza la ejecución para continuar lo más cercano posible al contexto del código especificado por `pCodeContext`, en el contexto del marco especificado por `pStackFrame`.  Cualquiera de estos argumentos puede ser `NULL`, que representa el cuadro o el contexto actual.  
  
## Vea también  
 [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)