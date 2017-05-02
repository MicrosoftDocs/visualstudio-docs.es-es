---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
Determina si el llamador del motor de script puede controlar una excepción especificada.  
  
## Sintaxis  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### Parámetros  
 `pExcepInfo`  
 \[in\] puntero a una estructura de `EXCEPINFO` que contiene la información que se muestra si no se encuentra ningún controlador de excepciones.  
  
 `pvar`  
 \[in\] el valor de A asociado a la excepción, como el valor producido por un fragmento de `throw` .  Este parámetro puede ser `NULL`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El llamador puede controlar la excepción|  
|`E_FAIL`|El llamador no puede controlar la excepción.|  
  
## Comentarios  
 Si una llamada a `IDispatchEx::InvokeEx`, o un método similar, produce una excepción, el motor de scripts un llamador en la cadena del llamador de script que admite la interfaz de `ICanHandleException` e indica que puede controlar la excepción.  Si ningún llamador puede controlar la excepción, el alto del motor de script.  
  
## Vea también  
 [ICanHandleException \(Interfaz\)](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)